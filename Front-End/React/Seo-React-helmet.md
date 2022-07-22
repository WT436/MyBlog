## Seo với React-Helmet trong React
- với file .js thì thằng helmet này không sảy ra vấn đề gì nhưng khi chuyển hướng lên tsx thì sẽ không nhận file

## solution

- file package.json

 "@types/react-helmet": "^6.1.0",
 "gatsby-plugin-react-helmet": "^4.7.0",
 "react-helmet": "^6.1.0",
 "react-scripts": "3.4.3",
 "typescript": "^4.1.2",
- create file : gatsby-config.js

 ```js
 module.exports = {
    plugins: [`gatsby-plugin-react-helmet`]
  }
 ```
 
 => xóa file node_modules
 yarn install