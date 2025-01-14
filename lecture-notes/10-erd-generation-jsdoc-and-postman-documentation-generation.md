# 10: ERD Generation, JSDoc and Postman Documentation Generation

## ERD Generation

Instead of using online tools like **Draw.io** and **Lucidchart** to create **ERD** diagrams, you can a library called **prisma-erd-generator** to generate **ERD** diagrams.

### Getting Started

To install **prisma-erd-generator**, run the following command in your terminal.

```bash
npm install prisma-erd-generator --save-dev
```

In the `schema.prisma` file, add the following code.

```javascript
generator erd {
  provider = "prisma-erd-generator"
}
```

Run the following command to generate the **ERD** diagram:

```bash
npx prisma generate
```

You should see an `.svg` file in the `prisma` directory. Open the file to view the **ERD** diagram.

You can customize the **ERD** diagram by adding the following code to the `schema.prisma` file.

```javascript
generator erd {
  provider = "prisma-erd-generator"
  output = "./prisma/erd.svg"
  theme = "forest"
}
```

**Resource:** <https://www.npmjs.com/package/prisma-erd-generator>

## JSDoc

**JSDoc** is an API documentation generator for **JavaScript**. **JSDoc** comments are written in a specific syntax to document the code. The **JSDoc** comments are then parsed and converted into HTML documentation. We will not convert the **JSDoc** comments into HTML documentation. However, it is good information to know.

### Getting Started

At the top of each file, add the following code.

```javascript
/**
 * @file <the purpose of the file>
 * @author <the name of the author>
 */
```

For example, in the `controllers/institution.js` file.

```javascript
/**
 * @file Manages all operations related to institutions
 * @author John Doe
 */
```

**Note:** `@fileoverview` or `@overview` can also be used instead of `@file`.

How do you comment a **function**?

```javascript
/**
 * @description This function creates a new institution
 * @param {object} req - The request object
 * @param {object} res - The response object
 * @returns {object} - The response object
 */
const createInstitution = async (req, res) => {
  try {
    await prisma.institution.create({
      data: { ...req.body },
    });

    const newInstitutions = await prisma.institution.findMany();

    return res.status(201).json({
      msg: "Institution successfully created",
      data: newInstitutions,
    });
  } catch (err) {
    return res.status(500).json({
      msg: err.message,
    });
  }
};
```

**Note:** Do not use **JSDoc** for in-line comments. Use normal JavaScript comments.

## Postman Documentation Generation

As you have progressed through the course, you have used **Postman** to test and document your API. **Postman** has a feature allowing you to generate API documentation.

### Getting Started

You can save your response as an example.

![](<../resources (ignore)/img/08/postman-1.PNG>)

You will see the following when you save your response as an example.

![](<../resources (ignore)/img/08/postman-2.PNG>)

Click on the **Collection**, then click on the **View complete collection documentation** link.

![](<../resources (ignore)/img/08/postman-3.PNG>)

Click on the **Publish** button.

![](<../resources (ignore)/img/08/postman-4.PNG>)

Scroll to the bottom of the page and click on the **Publish** button.

![](<../resources (ignore)/img/08/postman-5.PNG>)

Click on the **URL for published documentation** link.

![](<../resources (ignore)/img/08/postman-6.PNG>)

You have successfully published your documentation.

![](<../resources (ignore)/img/08/postman-7.PNG>)
