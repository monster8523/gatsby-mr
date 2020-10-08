---
title: Creating Nested Layout Components
typora-copy-images-to: ./
disableTableOfContents: true
---

ट्युटोरिअल पार्ट ३ मध्ये आपले स्वागत आहे.

## आपण काय पाहणार आहोत ह्या ट्युटोरिअल मध्ये?

या भागात आपण गॅटस्बी प्लगइन्स आणि "लेआउट" कॉम्पोनन्ट तयार करण्याबद्दल जाणून घेऊयात.

गॅटस्बी प्लगइन्स Javascript पॅकेजेस आहेत जी गॅटस्बी साइटवर कार्यक्षमता जोडण्यास मदत करतात. गॅटस्बी एक्सटेंसिबल म्हणून डिझाइन केले गेले आहे, याचा अर्थ असा आहे की गॅटस्बी जे काही करतो त्याबद्दल प्लगइन केवळ विस्तारित आणि सुधारित करण्यास सक्षम आहेत.

लेआउट कॉम्पोनन्ट आपल्या साइटच्या विभागांसाठी आहेत जे आपण एकाधिक पेज वर सामायिक करू इच्छित आहात. उदाहरणार्थ, साइट्समध्ये सामान्यत: सामायिक शीर्षलेख आणि footers असलेले लेआउट कॉम्पोनन्ट असतात. लेआउटमध्ये जोडण्यासाठी इतर सामान्य गोष्टी साइडबार आणि / किंवा नॅव्हिगेशन मेनू आहेत. या पेज वरील उदाहरणार्थ, शीर्षस्थानी शीर्षलेख gatsbyjs.org च्या लेआउट कॉम्पोनन्ट चा भाग आहे.

चला भाग तीन कडे जाऊ.

## प्लगइन वापरणे बाबत

आपण कदाचित प्लगइनच्या कल्पनांसह परिचित आहात. बऱ्याच सॉफ्टवेअर सिस्टम नवीन कार्यक्षमता जोडण्यासाठी सानुकूल प्लगइन जोडण्यास किंवा सॉफ्टवेअरच्या कोर वर्किंगमध्ये सुधारणा करण्यास सपोर्ट करतात. गॅटस्बी प्लगइन्स तशाच प्रकारे कार्य करतात.

(आपल्यासारखे!) कॉम्युनिटी मेंबर प्लगइनमध्ये योगदान देऊ शकतात (Javascript code, थोड्या प्रमाणात) जे नंतर गॅटस्बी साइट तयार करताना इतर सदस्य वापरू शकतील.

> आधीच शेकडो प्लगइन आहेत! गॅटस्बी [Plugin Library](/plugins/) एक्सप्लोर करा.

प्लगइन्ससह आमचे लक्ष्य ते स्थापित करणे आणि वापरणे सोपे करणे आहे. आपण कदाचित तयार करता त्या बहुतेक प्रत्येक गॅट्सबी साइटवर आपण प्लगइन वापरत असाल. उर्वरित ट्यूटोरियलमधून कार्य करीत असताना आपल्याकडे प्लगइन स्थापित करण्याची आणि वापरण्याची सराव करण्याची अनेक संधी उपलब्ध असतील.

प्लगइन्स वापरण्याच्या प्रारंभिक माहितीसाठी ही Typography.js साठी आपण गॅटस्बी प्लगइन स्थापित आणि कार्यान्वित करू.

[Typography.js](https://kyleamathews.github.io/typography.js/) एक Javascript लायब्ररी आहे जी आपल्या साइटच्या टायपोग्राफीसाठी जागतिक बेस शैली तयार करते.[corresponding Gatsby plugin](/packages/gatsby-plugin-typography/) लायब्ररी हे गॅटस्बी साइटवर वापरुन प्रवाहित करावे लागेल.

### ✋ नवीन गॅटस्बी साइट तयार करा

[part two](/tutorial/part-two/), आम्ही या टप्प्यावर नमूद केल्याप्रमाणे आपल्या डेस्कटॉपवर गोष्टी क्लीन ठेवण्यासाठी ट्यूटोरियलच्या मागील भागांमधील टर्मिनल विंडो आणि प्रोजेक्ट फाइल्स बंद करणे ही चांगली कल्पना आहे. 
नंतर एक नवीन टर्मिनल विंडो उघडा आणि commands `tutorial-part-three` नावाच्या नवीन गॅटस्बी साइट तयार करण्यासाठी पुढील आज्ञा चालवा आणि नंतर या नवीन command मध्ये जा:

```shell
gatsby new tutorial-part-three https://github.com/gatsbyjs/gatsby-starter-hello-world
cd tutorial-part-three
```

### ✋ इन्स्टॉल करा आणि कॉन्फिगर करा `gatsby-plugin-typography`

प्लगइन वापरण्यासाठी दोन मुख्य चरण आहेतः इन्स्टॉल करणे आणि कॉन्फिगर करणे.

1. इन्स्टॉल करा `gatsby-plugin-typography` NPM पॅकेज.

```shell
npm install --save gatsby-plugin-typography react-typography typography typography-theme-fairy-gates
```

> टीप: Typography.js ना काही अतिरिक्त पॅकेजेस आवश्यक आहेत, म्हणून त्या सूचनांमध्ये समाविष्ट केल्या आहेत. यासारख्या अतिरिक्त आवश्यकता प्रत्येक प्लगइनच्या "Install" सूचनांमध्ये सूचीबद्ध केल्या जातील.

2. आपल्या प्रोजेक्टच्या मुळाशी `gatsby-config.js` फाइल एडिट करा:

```javascript:title=gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: `gatsby-plugin-typography`,
      options: {
        pathToConfigModule: `src/utils/typography`,
      },
    },
  ],
}
```

`Gatsby-config.js` ही आणखी एक विशेष फाईल आहे जी गॅटस्बी आपोआप ओळखेल. येथे आपण प्लगइन आणि अन्य साइट कॉन्फिगरेशन जोडता येईल.

> आपली इच्छा असल्यास अधिक वाचण्यासाठी [doc on gatsby-config.js](/docs/gatsby-config/) पहा.

3. Typography.js ला कॉन्फिगरेशन फाईलची आवश्यकता आहे. `src` command `utils` नावाची नवीन command तयार करा. नंतर `utils` मध्ये `typography.js` नावाची एक नवीन फाईल जोडा आणि फाइलमध्ये खालील कॉपी करा:

```javascript:title=src/utils/typography.js
import Typography from "typography"
import fairyGateTheme from "typography-theme-fairy-gates"

const typography = new Typography(fairyGateTheme)

export const { scale, rhythm, options } = typography
export default typography
```

4. डेव्हलोपमेंट सर्व्हर प्रारंभ करा.

```shell
gatsby develop
```

एकदा आपण साइट लोड केल्यावर, आपण Chrome विकसक साधनांचा वापर करून HTML तपासणी केल्यास, आपणास असे आढळेल की टाइपोग्राफी प्लगिनने  CSS सह `<head>` कॉम्पोनन्ट मध्ये एक `<style>` कॉम्पोनन्ट जोडला:

![typography-styles](typography-styles.png)

### ✋ काही कन्टेन्ट आणि शैली बदल करा

आपल्या `src/pages/index.js` मध्ये खालील कॉपी करा जेणेकरून आपण ते पाहू शकता
Typography.js द्वारे जनरेट CSS चा परिणाम अधिक चांगल असे.

```jsx:title=src/pages/index.js
import React from "react"

export default () => (
  <div>
    <h1>Hi! I'm building a fake Gatsby site as part of a tutorial!</h1>
    <p>
      What do I like to do? Lots of course but definitely enjoy building
      websites.
    </p>
  </div>
)
```

आपली साइट आता यासारखी दिसली पाहिजे:

![no-layout](no-layout.png)

चला त्वरित सुधारणा करूया. बऱ्याच साइटवर पेज च्या मध्यभागी मध्यभागी मजकूराचा एकच कोलम असतो. हे तयार करण्यासाठी, खालील शैली `<div>`  मध्ये `src/pages/index.js`जोडा.

```jsx:title=src/pages/index.js
import React from "react"

export default () => (
  // highlight-next-line
  <div style={{ margin: `3rem auto`, maxWidth: 600 }}>
    <h1>Hi! I'm building a fake Gatsby site as part of a tutorial!</h1>
    <p>
      What do I like to do? Lots of course but definitely enjoy building
      websites.
    </p>
  </div>
)
```

![with-layout2](with-layout2.png)

छान! आपण आपले प्रथम गॅसबी प्लगइन स्थापित केले आणि कॉन्फिगर केले आहे!

## लेआउट कॉम्पोनन्ट तयार करणे

आता लेआउट कॉम्पोनन्ट बद्दल जाणून घेऊ. या भागासाठी सज्ज होण्यासाठी आपल्या प्रोजेक्टमध्ये दोन नवीन पेज जोडा: एक about पेज आणि एक contact पेज.

```jsx:title=src/pages/about.js
import React from "react"

export default () => (
  <div>
    <h1>About me</h1>
    <p>I’m good enough, I’m smart enough, and gosh darn it, people like me!</p>
  </div>
)
```

```jsx:title=src/pages/contact.js
import React from "react"

export default () => (
  <div>
    <h1>I'd love to talk! Email me at the address below</h1>
    <p>
      <a href="mailto:me@example.com">me@example.com</a>
    </p>
  </div>
)
```

चला नवीन about पेज कसे दिसते ते पाहूयाः

![about-uncentered](about-uncentered.png)

दोन नवीन पेजचे कन्टेन्ट अनुक्रमणिका पेज सारखी केंद्रित केली तर छान होईल. आणि जागतिक नेव्हिगेशन करणे चांगले होईल जेणेकरून व्हिसिटर्स प्रत्येक उप-पेज शोधणे आणि त्यांना भेट देणे सोपे होईल.

आपण आपला पहिला लेआउट कॉम्पोनन्ट तयार करुन या बदलांचा सामना कराल.

### ✋ आपला प्रथम लेआउट कॉम्पोनन्ट तयार करा

1. येथे एक नवीन डिरेक्टरी तयार करा `src/components`.

2. येथे एक मूलभूत लेआउट कॉम्पोनन्ट तयार करा `src/components/layout.js`:

```jsx:title=src/components/layout.js
import React from "react"

export default ({ children }) => (
  <div style={{ margin: `3rem auto`, maxWidth: 650, padding: `0 1rem` }}>
    {children}
  </div>
)
```

3. हा नवीन लेआउट कॉम्पोनन्ट आपल्या `src/pages/index.js` पेज कॉम्पोनन्ट इम्पोर्ट करा:

```jsx:title=src/pages/index.js
import React from "react"
import Layout from "../components/layout" // highlight-line

export default () => (
  <Layout> {/* highlight-line */}
    <h1>Hi! I'm building a fake Gatsby site as part of a tutorial!</h1>
    <p>
      What do I like to do? Lots of course but definitely enjoy building
      websites.
    </p>
  </Layout> {/* highlight-line */}
)
```

![with-layout2](with-layout2.png)

छान, लेआउट कार्यरत आहे! आपल्या अनुक्रमणिका पेज चे कन्टेन्ट अद्याप केंद्रित आहे.

परंतु यावर नेव्हिगेट करण्याचा प्रयत्न करा `/about/`, किंवा `/contact/`. त्या पेज चे कन्टेन्ट अद्याप केंद्रित होणार नाही.

4. या मध्ये लेआउट कॉम्पोनन्ट आयात करा `about.js` आणि `contact.js` (जसे आपण मागील चरणात केले `index.js`).

आपल्या तीनही पेज चे कन्टेन्ट या सामायिक केलेल्या लेआउट कॉम्पोनन्टबद्दल केंद्रित आहे!

### ✋ साइट शीर्षक जोडा

1.आपल्या नवीन लेआउट कॉम्पोनन्ट मध्ये पुढील ओळ जोडा:

```jsx:title=src/components/layout.js
import React from "react"

export default ({ children }) => (
  <div style={{ margin: `3rem auto`, maxWidth: 650, padding: `0 1rem` }}>
    <h3>MySweetSite</h3> {/* highlight-line */}
    {children}
  </div>
)
```

आपण आपल्या तीनपैकी कोणत्याही पेज वर गेल्यास आपल्याला समान शीर्षक जोडलेले दिसेल, उदा. `/about/` पृष्ठः

![with-title](with-title.png)

### ✋ पेज दरम्यान नेव्हिगेशन लाइन जोडा

1. आपल्या लेआउट कॉम्पोनन्ट फाइलमध्ये खालील कॉपी करा:

```jsx:title=src/components/layout.js
import React from "react"
// highlight-start
import { Link } from "gatsby"

const ListLink = props => (
  <li style={{ display: `inline-block`, marginRight: `1rem` }}>
    <Link to={props.to}>{props.children}</Link>
  </li>
)
// highlight-end

export default ({ children }) => (
  <div style={{ margin: `3rem auto`, maxWidth: 650, padding: `0 1rem` }}>
    {/* highlight-start */}
    <header style={{ marginBottom: `1.5rem` }}>
      <Link to="/" style={{ textShadow: `none`, backgroundImage: `none` }}>
        <h3 style={{ display: `inline` }}>MySweetSite</h3>
      </Link>
      <ul style={{ listStyle: `none`, float: `right` }}>
        <ListLink to="/">Home</ListLink>
        <ListLink to="/about/">About</ListLink>
        <ListLink to="/contact/">Contact</ListLink>
      </ul>
    </header>
    {/* highlight-end */}
    {children}
  </div>
)
```

![with-navigation2](with-navigation.png)

आणि तेथे आपण पूर्ण केले! मूलभूत जागतिक नेव्हिगेशनसह तीन पेज ची साइट.

_चालेन्ज:_ आपल्या नवीन "लेआउट कॉम्पोनन्ट" सामर्थ्यासह, आपल्या गॅटस्बी साइटमध्ये शीर्षलेख, footers, ग्लोबल नेव्हिगेशन, साइडबार इत्यादि जोडण्याचा प्रयत्न करा!

## पुढे काय येत आहे?

सुरू ठेवा [part four of the tutorial](/tutorial/part-four/) जिथे आपण गॅटस्बीच्या डेटा लेयरबद्दल आणि प्रोग्रामनुसार पेज तयार करण्यास शिकू शकाल!
