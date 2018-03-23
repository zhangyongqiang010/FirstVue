<template>
    <div id="layOut" v-cloak>
        <div class="bar">
            <a class="grid-icon" :class="{ 'active': layout == 'grid'}" @click="layout = 'grid'"></a>
            <a class="list-icon" :class="{ 'active': layout == 'list'}" @click="layout = 'list'"></a>
        </div>
        <ul v-if="layout == 'grid'" class="grid">
            <li v-for="a in articles">
                <a v-bind:href="a.url" target="_blank"><img :src="a.image.large" /></a>
            </li>
            <li class="clear"></li>
        </ul>
        <ul v-if="layout == 'list'" class="list">
            <li v-for="a in articles">
                <a v-bind:href="a.url" target="_blank"><img :src="a.image.small" /></a>
                <p>{{a.title}}</p>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'LayOut',
        data () {
            return {
                layout: 'grid',
                articles: [{
                    "title": "What You Need To Know About CSS Variables",
                    "url": "#",
                    "image": {
                        "large": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg",
                        "small": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg"
                    }
                },
                {
                    "title": "Freebie: 4 Great Looking Pricing Tables",
                    "url": "#",
                    "image": {
                        "large": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg",
                        "small": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg"
                    }
                },
                {
                    "title": "20 Interesting JavaScript and CSS Libraries for February 2016",
                    "url": "#",
                    "image": {
                        "large": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg",
                        "small": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg"
                    }
                },
                {
                    "title": "Quick Tip: The Easiest Way To Make Responsive Headers",
                    "url": "#",
                    "image": {
                        "large": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg",
                        "small": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg"
                    }
                },
                {
                    "title": "Learn SQL In 20 Minutes",
                    "url": "#",
                    "image": {
                        "large": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg",
                        "small": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg"
                    }
                },
                {
                    "title": "Creating Your First Desktop App With HTML, JS and Electron",
                    "url": "#",
                    "image": {
                        "large": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg",
                        "small": "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2708883094,2578579308&fm=27&gp=0.jpg"
                    }
                }]
            }

        }

    }
</script>
<style lang="scss" scoped>
    [v-cloak] {
    display: none;
    }
    li{
        list-style:none;
    }
    .bar{
        background-color:#5c9bb7;
        border-radius: 2px;
        padding: 10px;
        margin: 45px auto 25px;
        position:relative;
        text-align:right;
        line-height: 1;
    }
    .bar a{
        background:#4987a1 center center no-repeat;
        width:32px;
        height:32px;
        display:inline-block;
        text-decoration:none !important;
        margin-right:5px;
        border-radius:2px;
        cursor:pointer;
    }
    .bar a.active{
        background-color:#c14694;
    }
    .bar a.list-icon{
        background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyBpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMC1jMDYwIDYxLjEzNDc3NywgMjAxMC8wMi8xMi0xNzozMjowMCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNSBXaW5kb3dzIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOkYzNkFCQ0ZBMTBCRTExRTM5NDk4RDFEM0E5RkQ1NEZCIiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOkYzNkFCQ0ZCMTBCRTExRTM5NDk4RDFEM0E5RkQ1NEZCIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6RjM2QUJDRjgxMEJFMTFFMzk0OThEMUQzQTlGRDU0RkIiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6RjM2QUJDRjkxMEJFMTFFMzk0OThEMUQzQTlGRDU0RkIiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz7h1bLqAAAAWUlEQVR42mL8////BwYGBn4GCACxBRlIAIxAA/4jaXoPEkMyjJ+A/g9MDJQBRhYg8RFqMwg8RJIUINYLFDmBUi+ADQAF1n8ofk9yIAy6WPg4GgtDMRYAAgwAdLYwLAoIwPgAAAAASUVORK5CYII=);
    }

    .bar a.grid-icon{
        background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyBpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMC1jMDYwIDYxLjEzNDc3NywgMjAxMC8wMi8xMi0xNzozMjowMCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNSBXaW5kb3dzIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOjBEQkMyQzE0MTBCRjExRTNBMDlGRTYyOTlBNDdCN0I4IiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOjBEQkMyQzE1MTBCRjExRTNBMDlGRTYyOTlBNDdCN0I4Ij4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6MERCQzJDMTIxMEJGMTFFM0EwOUZFNjI5OUE0N0I3QjgiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6MERCQzJDMTMxMEJGMTFFM0EwOUZFNjI5OUE0N0I3QjgiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz4MjPshAAAAXklEQVR42mL4////h/8I8B6IGaCYKHFGEMnAwCDIAAHvgZgRyiZKnImBQsACxB+hNoDAQyQ5osQZIT4gH1DsBZABH6AB8x/JaQzEig++WPiII7Rxio/GwmCIBYAAAwAwVIzMp1R0aQAAAABJRU5ErkJggg==);
    }
    ul.grid{
        /* width: 570px; */
        display: inline-block;
        margin: 0 auto;
        text-align: left;
        
    }
    ul.grid li{
        padding: 2px;
        float:left;
    }
    .clear{
        clear: both;
    }
    ul.grid li img{
        width:270px;
        height:270px;
        object-fit: cover;
        display:block;
        border:none;
    }
    ul.list{
        margin: 0 auto;
        text-align: left;
    }

    ul.list li{
        border-bottom: 1px solid #ddd;
        padding: 10px;
        overflow: hidden;
    }

    ul.list li img{
        width:120px;
        height:120px;
        float:left;
        border:none;
    }

    ul.list li p{
        margin-left: 135px;
        font-weight: bold;
        color:#6e7a7f;
    }
</style>