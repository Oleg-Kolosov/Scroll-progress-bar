# Scroll-progress-bar

[watch](https://oleg-kolosov.github.io/Scroll-progress-bar/)

Put code below on youtube 🐒

```javascript
const options = {
    barStyles: {
        position: 'fixed',
        right: '2px',
        bottom: '2px',
        zIndex: '9999',
        display: 'grid',
        placeItems: 'center',
        width: '90px',
        height: '90px',
        borderRadius: '50%',
        backgroundColor: 'blue'
    },
    containerStyles: {
        display: 'flex',
        justifyContent: 'center',
        alignItems: 'center',
        width: '70px',
        height: '70px',
        fontSize: '1.2rem',
        backgroundColor: 'white',
        borderRadius: '50%'
    }
}

class ScrollProgressBar{
    constructor(options){
        this.options = options;
        this.init()
        this.setup()
    }

    init(){
        const bar = document.createElement("div")
        const container = document.createElement("div")
        const progress = document.createElement("p")

        Object.assign(bar.style, this.options.barStyles)
        Object.assign(container.style, this.options.containerStyles)

        progress.id = 'scroll-counter-progress'

        container.append(progress)
        bar.append(container)
        document.body.append(bar)
    }

    setup(){
        this.updateScrollProgress()
        window.addEventListener("scroll", this.updateScrollProgress)
    }

    calcProgress = () => {
        const html = document.documentElement
        const progressValue = html.scrollTop * 100 / (html.scrollHeight - html.clientHeight)
        return progressValue ? Math.round(progressValue) : 0
    }

    updateScrollProgress = () => {
        const progressValue = this.calcProgress()
        document.getElementById('scroll-counter-progress').textContent = `${progressValue}%`
    }

}

new ScrollProgressBar(options)
```
