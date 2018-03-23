<template>
  <div class="checkbox">
    <div class="radio">
      <label><input type="radio" v-model="sex" value="men">男</label>
      <label><input type="radio" v-model="sex" value="women">女</label>
      <p>已选择：{{ sex }}</p>
    </div>
    <div class="checked">
      <label><input type="checkbox" v-model="people.ming">小明</label>
      <label><input type="checkbox" v-model="people.hong">小红</label>
      <label><input type="checkbox" v-model="people.zhang">小张</label>
      <p>已选择：{{ people }}</p>
    </div>
    <div class="selected">
      <select v-model="selected">
        <option value="----">----</option>
        <option v-for="item in items" :value="item.value">{{ item.text }}</option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Chexckbox',
  data () {
    return {
      sex: 'men',
      people: {
        'ming': false,
        'hong': false,
        'zhang': false,
      },
      items: [
        {
          'text': 'A',
          'value': 'a'
        },
        {
          'text': 'B',
          'value': 'b'
        },
        {
          'text': 'C',
          'value': 'c'
        }
      ],
      selected:''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.checkbox {
  display: block;
  padding:20px;
  text-align: left;
  .radio {
    margin:20px 0px;
    p{
      margin: 20px 0px;
    }
  }
  .selected{
    margin: 30px;
    select{
      border: 1px solid #aaa;
      width: 300px;
    }
  }
}
</style>
