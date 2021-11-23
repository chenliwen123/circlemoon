<template>
  <div class="circlemoon">
    <div class="cdialog" v-if="value">
      <slot name="header"></slot> 
      <div class="cbody">
        <canvas id="canvas" ref="canvas">Canvas画板</canvas>
        <div class="autograph">
          <img :src="url" width="80" id="qianming123" height="50" alt />
        </div>
      </div>
      <div class="cfooter">
        <div class="cfooter_top">
          <div @click="eraser" class="eraser" :class="{showtextcolor:activetype == 'eraser'}">
            <svg t="1637562569932" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="6401" width="16" height="16">
            <path :style="activetype == 'eraser'?'fill: #409EFF;':''" d="M554.3 850.7L981 424c12.5-12.5 12.5-32.8 0-45.3L636.7 34.6c-12.5-12.5-32.8-12.5-45.3 0L90.5 535.5c-50 50-50 131 0 181l272.1 270.3c24 23.8 56.4 37.2 90.2 37.2H864c17.7 0 32-14.3 32-32s-14.3-32-32-32H599.5c-57 0-85.6-68.9-45.2-109.3z m71.1-736.9l276.4 276.4c6.2 6.2 6.2 16.4 0 22.6L607.9 706.6l-299-299 293.8-293.9c6.3-6.2 16.4-6.2 22.7 0.1zM135.8 580.7l127.9-127.9 299 299-127.9 127.9c-25 25-65.5 25-90.5 0L135.8 671.3c-25-25-25-65.6 0-90.6z" p-id="6402"></path></svg></div>
          <div class="operation_right">
            <span @click="houtui"><svg t="1637562259651" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="4627" width="16" height="16"><path d="M894.976 574.464q0 78.848-29.696 148.48t-81.408 123.392-121.856 88.064-151.04 41.472q-5.12 1.024-9.216 1.536t-9.216 0.512l-177.152 0q-17.408 0-34.304-6.144t-30.208-16.896-22.016-25.088-8.704-29.696 8.192-29.696 21.504-24.576 29.696-16.384 33.792-6.144l158.72 1.024q54.272 0 102.4-19.968t83.968-53.76 56.32-79.36 20.48-97.792q0-49.152-18.432-92.16t-50.688-76.8-75.264-54.784-93.184-26.112q-2.048 0-2.56 0.512t-2.56 0.512l-162.816 0 0 80.896q0 17.408-13.824 25.6t-44.544-10.24q-8.192-5.12-26.112-17.92t-41.984-30.208-50.688-36.864l-51.2-38.912q-15.36-12.288-26.624-22.016t-11.264-24.064q0-12.288 12.8-25.6t29.184-26.624q18.432-15.36 44.032-35.84t50.688-39.936 45.056-35.328 28.16-22.016q24.576-17.408 39.936-7.168t16.384 30.72l0 81.92 162.816 0q5.12 0 10.752 1.024t10.752 2.048q79.872 8.192 149.504 41.984t121.344 87.552 80.896 123.392 29.184 147.456z" p-id="4628"></path></svg></span>
            <span @click="qianjin"><svg t="1637562297351" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="5498" width="16" height="16"><path d="M108.544 572.416q0-77.824 29.184-147.456t80.896-123.392 121.344-87.552 149.504-41.984q10.24-3.072 21.504-3.072l162.816 0 0-81.92q1.024-20.48 16.384-30.72t39.936 7.168q7.168 5.12 27.648 20.992t45.568 35.84 50.688 40.448 44.032 35.84q16.384 13.312 28.672 26.624t12.288 25.6q0 14.336-10.752 24.064t-26.112 22.016l-51.2 38.912q-26.624 19.456-50.688 36.864t-42.496 30.208-26.624 16.896q-15.36 9.216-26.112 11.776t-17.408-0.512-10.24-10.24-3.584-15.36l0-81.92-162.816 0-5.12 0q-50.176 5.12-93.184 26.112t-75.264 54.784-50.688 76.8-18.432 92.16q0 52.224 20.48 97.792t56.32 79.36 83.968 53.76 102.4 19.968l158.72-1.024q16.384 0 33.28 6.144t29.696 16.384 20.992 24.064 8.192 30.208q0 15.36-8.192 29.696t-22.016 24.576-30.72 16.384-33.28 6.144l-177.152 0-9.216 0q-4.096 0-9.216-1.024-80.896-7.168-151.04-41.472t-121.856-88.064-81.408-123.392-29.696-148.48z" p-id="5499"></path></svg></span>
          </div>
        </div>
        <div class="cfooter_bottom">
          <div @click="biaozhu('line')" :class="{showtextcolor:activetype == 'line'}">
            <svg t="1637562932200" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="9577" width="20" height="20">
            <path :style="activetype == 'line'?'fill: #409EFF;':''" d="M852.8 365c-71.6 11.8-188.4 15-266-132.2-83.2-158.2-217.6-163-296.2-148.6-38.2 7-66.8 39-66.8 70l0 393.2c22.6 8.6 46.8-0.4 53-1.6 1.6-0.4 3-0.6 4.8-1 50-11 102.8-16.2 233.6 46.6 164 78.6 307.6-66.2 363.2-167 4-7 17.4-40.4 17.4-72.4C876.4 360 852.8 365 852.8 365z" p-id="9578"></path><path d="M176 64 144 64c-8.8 0-16 7.2-16 16l0 864c0 8.8 7.2 16 16 16l32 0c8.8 0 16-7.2 16-16L192 80C192 71.2 184.8 64 176 64z" p-id="9579"></path></svg>
            <span>标注</span>
            </div>
          <div @click="wenzi('text')" :class="{showtextcolor:activetype == 'text'}">
            <svg t="1637563237000" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="10564" width="20" height="20">
            <path :style="activetype == 'text'?'fill: #409EFF;':''" d="M790.754133 93.866667C867.733333 93.866667 930.133333 156.266667 930.133333 233.245867v557.508266C930.133333 867.733333 867.733333 930.133333 790.754133 930.133333H233.245867C156.266667 930.133333 93.866667 867.733333 93.866667 790.754133V233.245867C93.866667 156.266667 156.266667 93.866667 233.245867 93.866667h557.508266zM389.768533 775.8336a12.8 12.8 0 0 0-12.8 12.8v11.246933a12.8 12.8 0 0 0 13.4272 12.7872c31.786667-1.565867 54.3232-2.594133 67.613867-3.0848 22.638933-0.832 41.1776-1.250133 55.624533-1.250133 19.997867 0 57.220267 1.250133 111.6672 3.7504a54795.541333 54795.541333 0 0 0 18.030934 0.725333 12.8 12.8 0 0 0 12.8-12.8v-11.374933a12.8 12.8 0 0 0-12.8-12.8h-1.783467c-16.110933 0-28.608-1.527467-37.499733-4.5824-8.887467-3.054933-15.415467-8.055467-19.584-15.0016-3.6096-7.223467-6.2464-18.193067-7.914667-32.917333-1.664-14.72-2.500267-40.413867-2.500267-77.0816v-77.917867c0-38.144 0.1408-88.285867 1.92-269.0304a12.8 12.8 0 0 1 12.8-12.637867h60.6976c42.496 0 70.971733 5.905067 85.418667 17.706667 8.6528 7.0784 17.2672 26.244267 25.847467 57.5104a12.8 12.8 0 0 0 14.3104 9.258667l13.824-2.1504a12.8 12.8 0 0 0 10.7392-14.203734c-3.349333-27.323733-5.546667-47.735467-6.600534-61.243733a867.592533 867.592533 0 0 1-2.705066-67.293867 10.082133 10.082133 0 0 0-12.322134-9.8304c-11.434667 2.606933-22.1184 4.288-32.055466 5.038934-20.138667 1.527467-55.765333 2.2912-106.875734 2.2912H389.051733c-45.559467 0-77.917867-0.763733-97.083733-2.2912-9.028267-0.7168-19.0976-2.210133-30.208-4.48a12.8 12.8 0 0 0-15.330133 11.682133c-1.719467 25.5232-3.554133 45.346133-5.504 59.464533-2.039467 14.7584-6.1056 36.928-12.202667 66.5088a12.8 12.8 0 0 0 9.877333 15.104l15.240534 3.242667a12.8 12.8 0 0 0 14.856533-8.631467c10.282667-32.221867 20.258133-52.0064 29.934933-59.349333 16.110933-12.219733 45.973333-18.3296 89.582934-18.3296h58.8672a12.8 12.8 0 0 1 12.8 12.8v225.531733c0 81.109333-0.554667 136.6656-1.664 166.664534-1.109333 30.0032-3.0592 48.891733-5.8368 56.669866-4.164267 10.274133-10.555733 17.429333-19.165867 21.457067s-22.2208 6.0416-40.832 6.0416h-2.615467z" fill="#2c2c2c" p-id="10565"></path></svg>
            <span>文字</span>
            </div>
          <div @click="qianming">
            <svg t="1637563326108" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="14265" width="20" height="20"><path d="M975.60576 121.48736a159.49824 159.49824 0 0 0-53.39136-11.53024c-62.8736-10.40384-148.23424 5.59104-215.7568 40.3456 19.94752-46.73536-55.9104-26.27584-84.84864-19.0464-92.89728 23.12192-176.47616 64.86016-250.85952 121.856 6.5536-39.66976-45.71136-16.54784-83.18976 13.23008-73.87136 58.69568-132.56704 128.73728-168.42752 213.52448-31.9488 75.48928-31.68256 151.9616-3.03104 223.15008 96.89088-102.44096 188.98944-200.47872 307.56864-299.02848 132.7104-110.34624 291.4304-195.2768 383.42656-202.9568-347.05408 167.56736-576.512 444.5184-799.76448 727.4496h386.68288v-14.25408H48.08704c6.77888-2.72384 12.9024-6.90176 17.89952-12.24704 25.76384-26.95168 46.83776-58.08128 74.09664-83.72224 34.36544-32.31744 36.37248-29.65504 65.90464-30.39232 57.46688-1.4336 115.67104-5.4272 172.09344-15.36 120.05376-21.03296 222.57664-73.56416 300.9536-164.18816 19.59936-22.65088 38.5024-61.0304-11.93984-59.55584 17.75616-8.0896 30.5152-12.94336 42.25024-19.2512 92.0576-49.11104 177.39776-105.39008 231.40352-194.4576 14.62272-23.9616 31.31392-69.95968-18.0224-60.96896 27.136-25.43616 54.02624-46.3872 75.3664-71.41376 31.92832-37.1712 23.61344-62.7712-22.48704-81.18272z" p-id="14266"></path></svg>
            <span>签名</span>
            </div>
          <div @click="clear">
            <svg t="1637563622192" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="33503" width="20" height="20"><path d="M889.263158 431.157895v501.221052c0 26.947368-26.947368 43.115789-59.284211 43.11579H188.631579c-32.336842 0-53.894737-21.557895-53.894737-43.11579V431.157895h97.010526v447.326316h560.505264V431.157895v-10.778948c0-26.947368 21.557895-48.505263 48.505263-48.505263s48.505263 21.557895 48.505263 48.505263V431.157895z m-97.010526 0c5.389474 21.557895 21.557895 37.726316 48.505263 37.726316 21.557895 0 43.115789-16.168421 48.505263-37.726316v501.221052c0 26.947368-26.947368 43.115789-59.284211 43.11579H188.631579c-32.336842 0-53.894737-21.557895-53.894737-43.11579V431.157895v-10.778948c0-26.947368 21.557895-48.505263 48.505263-48.505263s48.505263 21.557895 48.505263 48.505263v458.105264h560.505264V431.157895z m0 447.326316h43.115789c-16.168421 0-43.115789 16.168421-43.115789 53.894736v-53.894736z m-560.505264 53.894736c0-37.726316-21.557895-53.894737-43.115789-53.894736h43.115789v53.894736z m0-53.894736H188.631579c16.168421 0 43.115789 16.168421 43.115789 53.894736v-53.894736z m560.505264 0h43.115789c-16.168421 0-43.115789 16.168421-43.115789 53.894736v-53.894736zM398.821053 377.263158c26.947368 0 48.505263 21.557895 48.505263 48.505263v334.147368c0 26.947368-21.557895 48.505263-48.505263 48.505264s-48.505263-21.557895-48.505264-48.505264V425.768421c0-26.947368 21.557895-48.505263 48.505264-48.505263z m215.578947 0c26.947368 0 48.505263 21.557895 48.505263 48.505263v334.147368c0 26.947368-21.557895 48.505263-48.505263 48.505264s-48.505263-21.557895-48.505263-48.505264V425.768421c0-26.947368 21.557895-48.505263 48.505263-48.505263zM75.452632 215.578947h873.094736c26.947368 0 48.505263 21.557895 48.505264 48.505264s-21.557895 48.505263-48.505264 48.505263H75.452632c-26.947368 0-48.505263-21.557895-48.505264-48.505263S48.505263 215.578947 75.452632 215.578947zM291.031579 118.568421c32.336842 0 48.505263-21.557895 48.505263-43.115789v43.115789h-48.505263z m48.505263 0h344.926316V215.578947H781.473684V75.452632c0-32.336842-21.557895-53.894737-48.505263-53.894737H291.031579c-26.947368 0-48.505263 26.947368-48.505263 53.894737V215.578947h97.010526V118.568421z m344.926316-43.115789c0 21.557895 16.168421 43.115789 48.505263 43.115789h-48.505263v-43.115789z m0 43.115789V215.578947H781.473684V75.452632c0-32.336842-21.557895-53.894737-48.505263-53.894737H291.031579c-26.947368 0-48.505263 26.947368-48.505263 53.894737V215.578947h97.010526V118.568421h344.926316z" p-id="33504"></path></svg>
            <span>清空</span>
            </div>
        </div>
        <div class="peizhi" v-if="activetype == 'line' || activetype == 'text'">
          <div class="colors">
            <div v-for="(item,index) in colors" :class="{active:index==activeindex}" :style="'background:'+item" :key="index" @click="uptatec(item,index)"></div>
          </div>
          <!-- <div class="options">
            <svg t="1631239808086" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2772" width="25" height="25"><path d="M896 812.9 594.2 511.1l301.2-301.2-82.3-82.3L511.9 428.8l-301-301L128.6 210.1l301 301L128 812.7l82.3 82.3 301.6-301.6 301.8 301.8L896 812.9zM896 812.9" p-id="2773"></path></svg>
            <svg t="1631239764679" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2487" width="30" height="30"><path d="M416.832 798.08C400.64 798.08 384.512 791.872 372.16 779.52L119.424 525.76C94.784 500.992 94.784 460.8 119.424 436.032 144.128 411.264 184.128 411.264 208.768 436.032L416.832 644.928 814.4 245.76C839.04 220.928 879.04 220.928 903.744 245.76 928.384 270.528 928.384 310.656 903.744 335.424L461.504 779.52C449.152 791.872 432.96 798.08 416.832 798.08Z" p-id="2488"></path></svg>
          </div> -->
        </div>
      </div>
      
      <textarea name="textarea" id="textarea" cols="30" rows="1" style="font-size: 26px;" :style="'color:'+colors[activeindex]"></textarea>
    </div>
    
  </div>
</template>

<script>
import {enableUndo} from 'undo-canvas'
var draw,tempbindfun,eraserfunbind;
var preHandler = function(e) {
  console.log(2)
  // e.preventDefault();
};
class Draw {
  constructor(el) {
    this.el = el;
    this.canvas = document.getElementById(this.el);
    this.cxt = this.canvas.getContext("2d");
    this.stage_info = canvas.getBoundingClientRect();
    this.path = {
      beginX: 0,
      beginY: 0,
      endX: 0,
      endY: 0
    };
    this.nowstate = '';
    this.newcolor=''
    this.textarea = document.querySelectorAll('.cdialog #textarea')[0];
    tempbindfun = this.drawing.bind(this);
    eraserfunbind = this.eraserfun.bind(this);
  }
  init(btn) {
    var that = this;
    this.canvas.addEventListener("touchstart", function(event) {
      document.addEventListener("touchstart", preHandler, false);
      that.cxt.putTag();
      if(that.nowstate == 'line'){
        that.drawBegin(event);
      }else if(that.nowstate == 'text'){
        that.appendtext(event)
      }else{

      }
    });
    this.canvas.addEventListener("touchend", function(event) {
      document.addEventListener("touchend", preHandler, false);
      that.cxt.putTag();
      that.drawEnd();
    });
    this.clear(btn);
    enableUndo(this.cxt)

  }
  appendtext(e){
    this.canvas.removeEventListener("touchmove",tempbindfun,false)
    if(this.textarea.style.display == "block"){
      this.textarea.blur();
      return false
    }
    this.textarea.style.display="block"
    this.textarea.setAttribute('rows',1)
    this.textarea.style.top = e.changedTouches[0].clientY +'px'
    this.textarea.style.left = e.changedTouches[0].clientX +'px'
    this.textarea.focus()
    let self = this;
    this.textarea.onblur = function(){
      self.cxt.font=`${self.textarea.style.fontSize} Verdana`;
      let row = self.textarea.value.split('\n');
      self.cxt.fillStyle = self.newcolor;
      row.forEach( (item,index) => {
        self.cxt.fillText(item,self.textarea.offsetLeft-self.stage_info.left,self.textarea.offsetTop + (index*self.textarea.style.fontSize.split('px')[0]) - self.stage_info.top);
      })
      self.textarea.value = ''
      self.cxt.putTag();
      self.textarea.style.display = "none"
    }
    this.textarea.oninput = function(){
      self.textarea.setAttribute('rows',self.textarea.value.split('\n').length)
      // self.textarea.row = self.textarea.value.split('\n').length
    }
  }
  drawBegin(e) {
    var that = this;
    window.getSelection()
      ? window.getSelection().removeAllRanges()
      : document.selection.empty();
    this.cxt.strokeStyle = this.newcolor;
    this.cxt.beginPath();
    this.cxt.moveTo(
      e.changedTouches[0].clientX - this.stage_info.left,
      e.changedTouches[0].clientY - this.stage_info.top
    );
    this.path.beginX = e.changedTouches[0].clientX - this.stage_info.left;
    this.path.beginY = e.changedTouches[0].clientY - this.stage_info.top;
    this.canvas.removeEventListener("touchmove",eraserfunbind,false)
    this.canvas.addEventListener("touchmove",tempbindfun,false);
  }
  
  drawing(e) {
    this.cxt.lineTo(
      e.changedTouches[0].clientX - this.stage_info.left,
      e.changedTouches[0].clientY - this.stage_info.top
    );
    this.path.endX = e.changedTouches[0].clientX - this.stage_info.left;
    this.path.endY = e.changedTouches[0].clientY - this.stage_info.top;
    this.cxt.stroke();
  }
  eraser(){
    this.canvas.removeEventListener("touchmove",tempbindfun,false)
    this.canvas.addEventListener("touchmove",eraserfunbind,false);
  }
  eraserfun(e) {
    let x = e.changedTouches[0].clientX - this.stage_info.left;
    let y = e.changedTouches[0].clientY - this.stage_info.top;
    this.cxt.clearRect(x-10,y-10,20,20)
  }
  drawEnd() {
    document.removeEventListener("touchstart", preHandler, false);
    document.removeEventListener("touchend", preHandler, false);
    document.removeEventListener("touchmove", preHandler, false);
  }
  clear(x,y) {
    this.cxt.clearRect(0, 0, x, y);
  }
  save() {
    const canvasList = Array.prototype.slice.call(document.querySelectorAll('.cdialog canvas')).reverse();
    const newCanvas = document.createElement('canvas')
    newCanvas.width = this.domwidth
    newCanvas.height = this.domheight
    const context = newCanvas.getContext('2d')
    canvasList.forEach(item => {
      context.drawImage(item, 0, 0, this.domwidth, this.domheight)
    })
    return newCanvas.toDataURL('image/png')
  }
}
export default {
  props:{
    dom:{
      domparent:null,
      domwidth:0,
      domheight:0,
    },
    value:{
      type:Boolean,
      default:false
    },
  },
  name: 'circlemoon',
  watch:{
    value(){
      if(this.value == true){
        this.$nextTick( () => {
          this.domparent = this.dom.parentElement
          document.querySelector('.cbody').append(this.dom)
          this.domwidth = this.dom.offsetWidth
          this.domheight = this.dom.offsetHeight
          let canvas = document.getElementById('canvas')
          canvas.width = this.domwidth
          canvas.height = this.domheight
          // canvas.width = '100%';
          // canvas.height = '100%';
          this.$nextTick( () => {
            draw = new Draw("canvas");
            draw.init();
          });
        });
      }else{
        this.domparent.append(this.dom)
      }
    }
  },
  components: {  },
  directives: {  },
  data() {
    return {
      activeindex:4, // 当前激活的颜色
      activetype:'',
      colors:['#1c1c1c','#feff0a','#ffa109','#f16707','#ff0103','#ff00f6','#9914e4','#0e00f3','#00ff0b'],
      domwidth:'',
      domheight:'',
      url: "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFAAAAAyCAYAAADLLVz8AAAAAXNSR0IArs4c6QAAAxpJREFUaEPtmD2sTkEQhp9b0mokREQjKq2EGoWKQoFKIaG6hUoQRKVQSSgkEhQKotWTKESvU1CqtTLJGVmb852d3ffIvcV8zU1uzuzuPPPOz+4W+ZMIbEnWaUwCFEWQABOgSEA0TwUmQJGAaJ4KTIAiAdE8FZgARQKieSowAYoERPPdrMDbk28PRB/d/CjwBrgBfFppzf9yF94DPAZ+AqPO2xqngffAHWGdktNB4BFwDLgIfFsDYo8CHcy1auNnwDbwe/r/mpG+BNxc0eF9wOtJgaPB/cf9EYC2gAGz35zSok67M2dEJXwAbM/rwH1xLTcPq14BeKioKYeBVx2HP7VmHZrZN1pG/DsXhWdR2BUF4HngyhT9X9OOJ4EnAylndtY0TEm+1iYnoiXC1jtQlZd6TTmlRwHeAh5WjaKO5t6p3ryc/i5F1cCZgiPK9G9baRYJpn3zMbjv7PlHAT4FXlQjQa0Mj24EoH/7vaEYD9KJgMoj6jKVGsSI8lcF+BWwFC43rg/TA9AOZ/YXGmA8SJ8boN1ZO19dZuq50EYb68xDP1WBb6cZrbejzqWqp9PlBYd6Ut2ALKlQVp9tMArQxhhT4NKM1qvAVhp7+lrH70m5uTon1z6XqwLQm4Rdi+aG0l6ArTT29HXV96RcWR7Mzq50UuquAdAH6XKGMievAneBsgu/A+4BzxtXKE/RuTTuTd8ScF1ilspET2CkFLahs5y1aqAlwC9T1FvFf1OTaKV3xGkPgH3rt5fWzNlcV0lhB+aPBq0uHBkrNtW5SIPZ5Kzvu3/q8J7CxwFZiSMAy8cEj+TZmYYyVwMjxduUcm5a7wcw2jzKtF0qCQY0MsCvOgeWry9+UGsk5TvbpiZigI50PFE59NbNo5z9/F4eAVOmdnSPvzBHFFg2jaUa4fVsU7crD96sNY0PTGEWFHuNqZ/XomuXig2DXBug1cHySWnUmajTO/5dD8AdP+xuPEACFKOSABOgSEA0TwUmQJGAaJ4KTIAiAdE8FZgARQKieSowAYoERPNUYAIUCYjmqcAEKBIQzVOBCVAkIJr/AcVo4TMd95+QAAAAAElFTkSuQmCC",
    };
  },

  mounted() {
  },

  methods: {
    eraser(){
      this.activetype = 'eraser'
      draw.nowstate = 'eraser'
      draw.eraser();
    },
    uptatec(item,index){
      this.activeindex = index
      draw.newcolor = item
    },
    qianjin(){
      draw.cxt.redoTag();
    },
    houtui(){
      draw.cxt.undoTag()
    },
    clear: function() {
      draw.clear(this.domwidth,this.domheight);
      this.activetype = ''
    },
    wenzi(type){
      draw.nowstate = type
      this.activetype = type
      draw.newcolor = this.colors[this.activeindex]
    },
    biaozhu(type){
      draw.nowstate = type
      this.activetype = type
      draw.newcolor = this.colors[this.activeindex]
    },
    qianming(){
      draw.cxt.drawImage(document.getElementById('qianming123'),this.domwidth-80,this.domheight-50)
      draw.cxt.putTag();
      this.activetype = ''
    },
    save: function() {
      var data = draw.save.bind(this)();
      this.url = data;
      this.img = data
      return data
    },
  },
};
</script>

<style lang="scss">
.circlemoon{
  width: 100%;
  .cdialog{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content:space-between;
    position:fixed;
    top:0px;
    left:0px;
    background: #EBEEF5;
    #textarea{  
      position:absolute;
      display:none;
      z-index:9999;
      background:transparent;
      width:160px;
    }
    #qianming123{
      display: none;
    }
    .cbody{
      display:flex;
      justify-content:center;
      position: relative;
      height: calc(100% - 40vw);
      overflow:auto;
      #canvas{
        z-index: 9;
        position: absolute;
      }
      .autograph{
        position:absolute;
        bottom: 0;
        right: 0;
        display:flex;
        justify-content: center;
        align-items: center;
      }
    }
    .cfooter{
      display: flex;
      width:100%;
      flex-direction: column;
      justify-content: space-between;
      position:absolute;
      left:0;
      bottom: 0;
      .cfooter_top{
        display: flex;
        width:calc(100% - 30px);
        justify-content: space-between;
        margin:0 15px;
        .eraser{
          width:50px;
          height:50px;
          margin-left:0;
          background:#fff;
          border-radius: 30px;
          padding:6px 8px;
          box-shadow: 0px 4px 20px #ddd;
          display: flex;
          justify-content: center;
          align-items: center;
        }
        .operation_right{
          display: flex;
          span{
            width:50px;
            height:50px;
            margin-left:15px;
            background:#fff;
            border-radius: 30px;
            padding:6px 8px;
            box-shadow: 0px 4px 20px #ddd;
            display: flex;
            justify-content: center;
            align-items: center;
          }
        }
      }
      .cfooter_bottom{
        display: flex;
        justify-content: space-around;
        margin-top:40px;
        background: #fff;
        div{
          padding:14px 0;
          width: 100%;
          display: flex;
          justify-content: center;
          flex-wrap: wrap;
          span{
            width:100%;
            text-align: center;
            margin-top:5px;
          }
        }
      }
      .peizhi{
        display: flex;
        flex-wrap: wrap;
        width:100%;
      }
      .options{
        display: flex;
        justify-content: space-between;
        align-items:center;
        width:100%;
        padding:0 20px;
      }
      .colors{
        display: flex;
        width: 100%;
        align-items: center;
        padding:10px 20px;
        div{
          height: 30px;
          width:100%;
          flex:5;
          &.active{
            flex:6;
            height: 40px;
            border: 1px solid #9c9c9c;
          }
        }
      }
    }
  }
  .showtextcolor{
    color:#409EFF;
  }
}
</style>