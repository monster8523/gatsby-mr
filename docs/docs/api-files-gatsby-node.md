---
title: The gatsby-node.js API file
---

आपली साइट तयार करण्याच्या प्रक्रियेत एकदा `gatsby-node.js` फाइलमधील कोड चालविला जातो. आपण पेज डायनॅमिकली तयार करण्यासाठी, GraphQL नोड्स मध्ये जोडण्यासाठी किंवा बिल्ड लाइफसायकल दरम्यानच्या इव्हेंटला प्रतिसाद देण्यासाठी वापरू शकता. [Gatsby Node APIs](/docs/node-apis/) वापरण्यासाठी, आपल्या साइटच्या रूटमध्ये `gatsby-node.js` नावाची फाईल तयार करा.या फाईलमध्ये आपण वापरू इच्छित असलेले कोणतेही API निर्यात करा.

प्रत्येक Gatsby Node API [set of Node API helpers](/docs/node-api-helpers/) पास करते. हे आपल्याला अहवाल देण्यासारख्या अनेक पद्धतींमध्ये प्रवेश करू देते किंवा नवीन पेज तयार करण्यासारख्या क्रिया करण्यास प्रोत्साहन देते.

```js:title=gatsby-node.js
const path = require(`path`)
// Log out information after a build is done
exports.onPostBuild = ({ reporter }) => {
  reporter.info(`Your Gatsby site has been built!`)
}
// Create blog pages dynamically
exports.createPages = async ({ graphql, actions }) => {
  const { createPage } = actions
  const blogPostTemplate = path.resolve(`src/templates/blog-post.js`)
  const result = await graphql(`
    query {
      allSamplePages {
        edges {
          node {
            slug
            title
          }
        }
      }
    }
  `)
  result.data.allSamplePages.edges.forEach(edge => {
    createPage({
      path: `${edge.node.slug}`,
      component: blogPostTemplate,
      context: {
        title: edge.node.title,
      },
    })
  })
}
```
