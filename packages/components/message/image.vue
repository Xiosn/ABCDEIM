<script>
import close from '../../../assets/close.png'
export default {
  name: "lemonMessageImage",
  inheritAttrs: false,
  data() {
    return{
      isShow:false,
      content:"",
      img:close
    }
  },
  render() {
    return (
      <div>
        <lemon-message-basic
        class="lemon-message-image"
        props={{ ...this.$attrs }}
        scopedSlots={{
          content: props => <img style="max-width:100%;min-width:100px;display:block;" src={props.content} on-click={()=>{this.content=props.content;this.isShow=true}
          }/>
        }}
      />

      {this.isShow?<div style="position:absolute;left: -250px;right: -2px;top :-15px; padding: 0px 10px;padding-bottom:10px;z-index :9999;border-radius: 15px;border: #999;background :#fff;">
          <img style="width:25px;height:25px;margin:10px 0 0 740px;cursor:pointer;z-index:9999;" src={this.img} on-click={()=>{this.isShow=false}}/>
          <img style="max-width:100%;max-height:91%; width: auto; height: auto; padding-top:10px;z-index:99999" src={this.content}/>
      </div>:''}
      </div>
    );
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/utils/index'
+b(lemon-message-image)
  +b(lemon-message)
    +e(content)
      padding 0
      cursor pointer
      overflow hidden
</style>