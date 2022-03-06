My personal quick notes for Next.js for people knowing basics of React and Node.js

Thanks to [Maximilian Schwarzmüller](https://www.udemy.com/course/nextjs-react-the-complete-guide/#instructor-1) for this awesome [Udemy Course](https://www.udemy.com/course/nextjs-react-the-complete-guide/)

<details>   
<summary>Create a next app</summary>

```sh
npx create-next-app
```

start the development server

```sh
npm run dev
```

</details>

<details> 
<summary>File Based Routing</summary>

The **pages** directory is a special directory where we can write code for each page of our website.

The pages are generated based on the directory structure.

1. For each page we can opt to create a folder/file with same name. (as shown in image)

2. index.js is special file name that will be rendered on path to it's parent directory name. Hence both of these directory structure are same and will render on **/blogs** path (only use either one of them).

   **pages/blog/index.js**

   **pages/blog.js**

3. We can also define dynamic routes with special syntax file name.

   **[dynamic].js**

   Example:

   Directories - pages/blog/[id].js

   [id].js will be rendered for url **/blog/2321/**

4. Each file should export a react component for that page.

![file based routing](./img/fileBasedRouting.png)

<details><summary>How do I get the dynamic route value in my Component?</summary>

We have to use **useRouter** hook imported from next.

Example:-

The **query** property on router is a object that contains value of our dynamic route.

![dynamic route](./img/dynamicRoute.png)
![dynamic route Output](./img/dynamicRouteOutput.png)

</details>

<details><summary>Nested Dynamic Routes</summary>

Consider the following directory structure

Let's suppose there is a client with id = 123 and project id = 456

    /clients - this will load the index.js file present inside clients folder

    /clients/123 - this will load index.js file present inside [id] folder

    /clients/123/456 - this will load the [clientprojectid].js file

![nested dynamic routes](./img/nestedDynamicPaths.png)

</details>

<details><summary>Catch all routes</summary>
Suppose if we want to make a js file that is rendered for any path with any number of segments

Ex:-

    Suppose if we want to catch all such paths to the same file

    /blog/123
    /blog/123/456
    /blogs/123/456/789
    ...so on

For this we can create a special file inside blogs folder as shown in image. Note that the name of file can be anything but the three dots define it's a catch all route.

Also all the url segments can be accessed inside our react component using useRouter hook.

![catch all route](./img/catchAllRoute.png)

</details>

<details><summary>Clickable links for our routes</summary>

Now that we have created many routes. We have to create clickable buttons which helps us to navigate between all these routes without manually typing the routes or refreshing the page for each request.

- This can be done using the **Link** object imported from next.

![links](./img/links.png)

The **href** in Link can accept strings for paths however for bigger apps there might be very long paths which becomes cumbersome to write in form of pure strings.

Therefore there is another way of defining href inside Link. i.e we pass an object to href instead of string. This object has necessary information to which path a link should redirect to.

![link with object passed to href](./img/linkHref.png)

This format makes it easy to handle very big or complex routes.

- Another way to declare link is this syntax. The advantage here is you can give custom styling to your anchor tag. It functions the same as above.

![custom styled link](./img/linkCustomStyled.png)

</details>

 <details><summary>How to navigate programatically?</summary>
 
 This can be done easily with **useRouter** hook. 
 
 And just like **Link** here also we can pass either a string or an object to the path we want to navigate
 
 ![router push](./img/routerPush.png)
 ![router replace](./img/routerReplace.png)
 ![router push object](./img/routerPushObject.png)
 
 </details>
 
 <details><summary>404 Page</summary>
 This page is a specially named page which is rendered when user try to visit a non-existing route. 
 
 This is a special file and must be present inside pages folder with same name.
 
 ![404 page](./img/404Page.png)
 
 </details>
 
 **NOTE:-**
 
 The order of preference for the routes is
 
 	index.js > [dynamic].js > [...dynamic].js

</details>



<details> 
<summary>Regular React Components</summary>

Now that our routes are ready. We have to create react components that are not reachable from the routes but are used inside our app, these components are called regular components.

These components can be placed anywhere outside the **pages** folder. Prefreably create a folder named **components** parallel to our pages folder.

![regular components](./img/regularComponents.png)

The folder name is up to you and here you can place your regular components.

</details>
