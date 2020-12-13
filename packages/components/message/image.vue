<script>
import close from '../../icon/close.png'
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
          content: props => <img src={props.content} on-click={
            e=>{
              this.content=props.content;
              this.isShow=true
            }
          }/>
        }}
      />

      {this.isShow?<div class="box">
          <img style="width:25px;height:25px;margin:10px 0 0 740px;cursor:pointer;" src={this.img} on-click={()=>{this.isShow=false}}/>
          <img style="width:100%;height:91%; padding-top:10px;" src={this.content}/>
      </div>:''}
      </div>
    );
  }
};
</script>
<style lang="stylus">
@import '~styles/utils/index'
+b(lemon-message-image)
  +b(lemon-message)
    +e(content)
      padding 0
      cursor pointer
      overflow hidden
      img
        max-width 100%
        min-width 100px
        display block
.box {
  position absolute
  left -250px
  right -2px
  top -15px
  bottom -15px
  padding 0px 10px
  z-index 9999
  border-radius 15px
  border #999;
  background #fff
}
img {
  z-index:9999
  right 0
}
</style>
