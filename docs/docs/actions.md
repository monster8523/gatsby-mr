---
title: Actions
description: Documentation on actions and how they help you manipulate state within Gatsby
jsdoc:
  - "gatsby/src/redux/actions/public.js"
  - "gatsby/src/redux/actions/restricted.js"
contentsHeading: Functions
---

स्टेट व्यवस्थापित करण्यासाठी गॅटस्बी [Redux](http://redux.js.org) अंतर्गतरित्या वापरतो. जेव्हा आपण गॅट्सबी एपीआय अंमलात आणता, आपण क्रियांचा संग्रह पार करतो. 
[bindActionCreators](https://redux.js.org/api/bindactioncreators/) -जो आपण आपल्या साइटवर स्टेट  हाताळण्यासाठी वापरू शकता.

ऑब्जेक्ट `actions` फंक्शन्स असतात आणि हे स्वतंत्रपणे ES6 ऑब्जेक्ट डिस्ट्रक्चरिंगद्वारे काढले जाऊ शकतात.

```javascript
// For function createNodeField
exports.onCreateNode = ({ node, getNode, actions }) => {
  const { createNodeField } = actions
}
```
