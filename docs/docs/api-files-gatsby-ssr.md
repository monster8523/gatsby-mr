---
title: The gatsby-ssr.js API file
---

`Gatsby-ssr.js` फाइल आपल्याला स्थिर HTML फायलींची कन्टेन्ट बदलू देते कारण ते Gatsby आणि `Node.js` द्वारे सर्व्हर-साइड रेंडर (SSR) करण्यात येते. [Gatsby SSR APIs](/docs/ssr-apis/) वापरण्यासाठी, आपल्या साइटच्या रूटमध्ये `gatsby-ssr.js` नावाची फाईल तयार करा. या फाईलमध्ये आपण वापरू इच्छित असलेले कोणतेही API निर्यात करा.

 APIs `wrapPageElement` आणि `wrapRootElement` SSR आणि [ब्राऊझर APIs](/docs/browser-apis) दोन्हीमध्ये अस्तित्त्वात आहेत. जर आपण त्यापैकी एक वापरत असाल तर आपण दोन्हीमध्ये याचा वापर करावा  `gatsby-ssr.js` आणि `gatsby-browser.js` जेणेकरुन ब्राउझर `JavaScript` सह [hydrated](/docs/glossary#hydration) झाल्यानंतर `Node.js` सह SSR द्वारे तयार झालेले पेजेस एकसारखीच असतील.

```jsx:title=gatsby-ssr.js
const React = require("react")
const Layout = require("./src/components/layout")

// Adds a class name to the body element
exports.onRenderBody = ({ setBodyAttributes }, pluginOptions) => {
  setBodyAttributes({
    className: "my-body-class",
  })
}

// Wraps every page in a component
exports.wrapPageElement = ({ element, props }) => {
  return <Layout {...props}>{element}</Layout>
}
```
