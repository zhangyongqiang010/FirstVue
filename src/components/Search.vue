<template>
    <div id="search">
        <div class="bar">
        <!--v-modal的双向绑定-->
            <input type="text" v-model="searchStr" placeholder="输入你想要搜索的内容"/>
        </div>
        <ul>
        <!--这里使用了articles1来做特别标志,证明这个计算属性不是在data里面的,而是通过计算出来的-->
        <!--通过遍历计算属性articles1来输出需要的信息-->
            <li v-for="a in articles1">
                <a :href="a.url"><img :src="a.image"/></a>
                <span>{{a.title}}</span>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'Search',
        data () {
            return {
                searchStr: "",
                articles: [
                    {
                        "title": "What You Need To Know About CSS Variables",
                        "url": "http://tutorialzine.com/2016/03/what-you-need-to-know-about-css-variables/",
                        "image": "http://cdn.tutorialzine.com/wp-content/uploads/2016/03/css-variables-100x100.jpg"
                    },
                    {
                        "title": "Freebie: 4 Great Looking Pricing Tables",
                        "url": "http://tutorialzine.com/2016/02/freebie-4-great-looking-pricing-tables/",
                        "image": "http://cdn.tutorialzine.com/wp-content/uploads/2016/02/great-looking-pricing-tables-100x100.jpg"
                    },
                    {
                        "title": "20 Interesting JavaScript and CSS Libraries for February 2016",
                        "url": "http://tutorialzine.com/2016/02/20-interesting-javascript-and-css-libraries-for-february-2016/",
                        "image": "http://cdn.tutorialzine.com/wp-content/uploads/2016/02/interesting-resources-february-100x100.jpg"
                    },
                    {
                        "title": "Quick Tip: The Easiest Way To Make Responsive Headers",
                        "url": "http://tutorialzine.com/2016/02/quick-tip-easiest-way-to-make-responsive-headers/",
                        "image": "http://cdn.tutorialzine.com/wp-content/uploads/2016/02/quick-tip-responsive-headers-100x100.png"
                    },
                    {
                        "title": "Learn SQL In 20 Minutes",
                        "url": "http://tutorialzine.com/2016/01/learn-sql-in-20-minutes/",
                        "image": "http://cdn.tutorialzine.com/wp-content/uploads/2016/01/learn-sql-20-minutes-100x100.png"
                    },
                    {
                        "title": "Creating Your First Desktop App With HTML, JS and Electron",
                        "url": "http://tutorialzine.com/2015/12/creating-your-first-desktop-app-with-html-js-and-electron/",
                        "image": "http://cdn.tutorialzine.com/wp-content/uploads/2015/12/creating-your-first-desktop-app-with-electron-100x100.png"
                    }
                ]
            }
        },
        computed: { //使用计算属性
            articles1: function () { //这个articles1就是计算属性
                if(!this.searchStr){ //没有输入搜索项就不处理
                    return false;
                }
                //过滤带有空格的输入内容
                var s = this.searchStr.trim().toLowerCase();
                //使用js的filter遍历循环,通过在这里处理循环之后然后返回处理好的数组给v-for进行处理
                var result = this.articles.filter(function (item) {
                    if (item.title.toLowerCase().indexOf(s) !== -1) {
                        return item;
                    }
                });
                return result;
            }
        }
    }
</script>

<style lang="scss">
    #search{
        margin-top: 20px;
        display: block;
        .bar{
            input{
                padding: 0px 10px;
                border: 1px solid #aaa;
                height: 30px;
                width: 80%;
                outline: none;
            }
        }
    }
</style>

