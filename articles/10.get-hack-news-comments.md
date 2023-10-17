# 10.Get Hack News Comments

获取 HackNews 中特定 id 元素中的评论，并向上遍历评论，直到根评论

{% embed url="https://news.ycombinator.com/item?id=37848212" %}

```javascript
function getComments(id) {
    const element = document.getElementById(id)
    outputComments(element)
    let parentElement = getParent(element)
    while (parentElement) {
        outputComments(parentElement)
        parentElement = getParent(parentElement)
    }
}

function getParent(element) {
    const indentElement = element.querySelector('.ind')
    if (!indentElement) {
        return
    }
    const indent = indentElement.getAttribute('indent')
    let parentIndentElement = document.querySelector(`[indent="${Number(indent) - 1}"]`)
    if (!parentIndentElement) {
        return
    }
    return parentIndentElement.parentElement
}

function outputComments(element) {
    if (!element) {
        return
    }
    const commtextElement = element && element.querySelector('.commtext')
    const nodes = commtextElement && commtextElement.childNodes
    if (!nodes) {
        return
    }
    nodes.forEach(node => {
        console.info(node.textContent)
    })
}
```
