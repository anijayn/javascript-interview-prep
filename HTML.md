# HTML Questions

### What are the benefits of using semantic HTML5 elements and how does semantic markup impact accessibility and SEO?
Semantic HTML5 elements provide several benefits:
- **Improved Accessibility**: Semantic elements make web pages more accessible to users with disabilities. Screen readers can interpret the structure of the page and describe it to visually impaired users.
- **Better SEO**: Search engines can better understand the content of a page and its relevance to specific keywords.
- **Enhanced Readability**: Semantic elements make the HTML code more readable and easier to understand.
- **Consistent Structure**: Semantic elements provide a consistent structure for the content of a page, making it easier to style and maintain.

### How can you utilize custom data attributes in HTML to enhance JavaScript functionality? Can you provide an example of how to set and access these attributes?
Custom data attributes in HTML allow you to store arbitrary data on elements. This data can be accessed and manipulated using JavaScript. They are prefixed with `data-`
Example:
```html
<div data-custom-attribute="value">
    This is a custom data attribute.
</div>
```

```javascript
const element = document.querySelector('[data-custom-attribute]');
console.log(element.dataset.customAttribute); // "value"
```

### Why is it important to use the <label> element in forms and how does it improve accessibility?
For users who rely on screen readers, the label tag provides a clear description of each form control, making it easier to understand and interact with the form. Additionally, it enhances the user interface by allowing users to click on the label to focus or activate the associated form control.
