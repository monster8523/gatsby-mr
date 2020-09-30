---
title: The gatsby-browser.js API file
---

`Gatsby-browser.js` फाइल आपल्याला ब्राउझरमधील क्रियांना प्रतिसाद देऊ देते आणि अतिरिक्त घटकांमध्ये आपली साइट वापरु देते. The [[Gatsby ब्राउझर API](/docs/browser-apis)आपल्याला गॅट्सबीच्या [client-side](/docs/glossary#client-side) सह संवाद साधण्यासाठी बरेच पर्याय देते.

`wrapPageElement` आणि  `wrapRootElement` हे दोन्ही ब्राउझर मध्ये असित्वात आहेत  [Server-Side Rendering (SSR) APIs](/docs/ssr-apis).आपण त्यापैकी एखादा वापरत असल्यास, आपण दोन्ही `gatsby-ssr.js` आणि `gatsby-browser.js` जेणेकरुन SSR आणि Node.js केलेली पेज एकसारखीच असतील [hydrated](/docs/glossary#hydration) आणि ते ब्राउझर javascript मध्ये पण चालेल.

ब्राउझर API वापरण्यासाठी, आपल्या साइटच्या रुटशी एक फाईल तयार करा `gatsby-browser.js`.आणि आपण या फाईलमधून वापरू इच्छित असलेला प्रत्येक एपीआय निर्यात करा.

```jsx:title=gatsby-browser.js
const React = require("react")
const Layout = require("./src/components/layout")

// Logs when the client route changes
exports.onRouteUpdate = ({ location, prevLocation }) => {
  console.log("new pathname", location.pathname)
  console.log("old pathname", prevLocation ? prevLocation.pathname : null)
}

// Wraps every page in a component
exports.wrapPageElement = ({ element, props }) => {
  return <Layout {...props}>{element}</Layout>
}
```
