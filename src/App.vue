<script setup>
import { onMounted, reactive } from 'vue'
import StarTrails from './components/StarTrails.vue'

const data = reactive({
  titleList: [
    '热爱……',
    '敬畏之心！',
    '赞美之心！',
    '我很好奇！',
    '你好，请多指教',
    '*舒缓的现代音乐*',
    '希望能成为有趣的人',
    '相信美好的事情即将发生',
    '平凡的日常正奇迹的发生着',
    '你所热爱的<br/>就是你的生活',
    '给时光以生命<br/>给岁月以文明',
    '路虽远行则将至<br/>事虽难做则必成',
    '一望无际的迷雾中<br/>有人在寻找光明',
    '当你在凝视着网页的时候<br/>网页也正在凝视着你',
  ],
  navLinks: [{
    name: '首 页',
    link: 'https://cws.plus',
  }],

  myProjects: [
    {
      name: 'Home',
      description: '个人简介、主页、引导页',
      link: 'https://cws.plus',
    },
    {
      name: 'Blog',
      description: '个人博客',
      link: 'https://blog.cws.plus',
    },
    {
      name: 'Disk',
      description: '个人网盘',
      link: 'https://alist.cws.plus',
    },
    {
      name: 'Music',
      description: '音乐库',
      link: 'https://music.cws.plus',
    },
    {
      name: 'Status',
      description: '站点监控',
      link: 'https://stats.uptimerobot.com/sEkqLbF2Ha',
    }
  ],

  socialLinks: [{
    icon: '<i i-ant-design-github-outlined />',
    link: 'https://github.com/cwsya',
    label: 'Github',
  }, {
    icon: '<i i-ant-design-mail-outlined />',
    link: 'mailto:cwsya@qq.com',
    label: 'Mail',
  }, {
    icon: '<i i-ant-design-qq-outlined />',
    link: 'https://tenapi.cn/v2/qqcard?qq=2771628927',
    label: 'QQ',
  }],
})

onMounted(() => {
  // 背景固定
  window.addEventListener('scroll', () => {
    const bg = document.getElementById('background')
    const scrollTop = window.scrollY
    if (scrollTop > 0.7 * window.innerHeight)
      bg.classList.add('fixed')
    else
      bg.classList.remove('fixed')
  })
})
</script>

<template>
  <!-- 导航 -->
<!--  <nav absolute fixed bottom-4 left-4 z-20>-->
<!--    <div v-for="(item, index) in data.navLinks" :key="index" my-6 text-3 text-white wv>-->
<!--      <a :href="item.link" opacity-75 text-white tracking-widest hover:opacity-100>-->
<!--        {{ item.name }}-->
<!--      </a>-->
<!--    </div>-->
<!--  </nav>-->

  <!-- 主体 -->
  <main bg-transparent absolute w-full z-10>
    <!-- 个人简介 -->
    <section mx-9vw mt-15vw>
      <!-- 关于我 -->
      <div text-bold mb-4 ml-10 text-10 text-white>
        About Me
      </div>
      <div mx-10 mb-10 flex justify-between>
        <div class="text-white/80">
          <p leading-10>
            嗨，你好，我是陈文生。
          </p>
          <p leading-10>
            热爱计算机科学和 IT 互联网事业，希望能成为一名优秀的开发者。
          </p>
          <p leading-10>
            我们正在让这个世界变得更加美好，通过代码的重复使用和延展构建完美体系。
          </p>
          <p leading-10>
            We're making the world a better place. Through constructing elegant hierarchies for maximum code reuse and extensibility.
          </p>
        </div>
        <img hidden rounded-full h-30 w-30 transition md:block hover:-translate-y--2 src="./assets/images/avatar.jpg" alt="avatar">
      </div>


      <!-- 我的项目 -->
      <div text-bold mb-2 ml-10 text-8 text-white>
        Projects
      </div>
      <div mb-10 flex flex-wrap justify-between>
        <div v-for="(item, index) in data.myProjects" :key="index" mx-10 my-4 class="basis-3/4 md:basis-1/6">
          <a :href="item.link">
            <div class="bg-white/5 hover:bg-white/10" p-2 rounded-lg shadow-md flex-col transition backdrop-blur-3xl backdrop-opacity-60 hover:backdrop-opacity-100 hover:-translate-y-2>
              <div text-bold opacity-75 text-white>
                {{ item.name }}
              </div>
              <div mt-1 opacity-50 text-3 text-white>
                {{ item.description }}
              </div>
            </div>
          </a>
        </div>
      </div>

      <!-- 社交链接 -->
      <div text-bold mb-2 ml-10 text-8 text-white>
        Find Me
      </div>
      <div flex flex-wrap justify-between>
        <div v-for="(item, index) in data.socialLinks" :key="index" mx-10 my-4 class="basis-1/6">
          <a class="bg-white/5 hover:bg-white/10" p-2 rounded-lg shadow-md flex-col justify-between items-center transition backdrop-blur-3xl backdrop-opacity-60 hover:backdrop-opacity-100 hover:-translate-y-2 :href="item.link" target="_blank">
            <div mb-1 text-white f-c-c v-html="item.icon" />
            <div text-bold opacity-75 text-white>{{ item.label }}</div>
          </a>
        </div>
      </div>
    </section>

    <!-- 底部 -->
    <footer mb-5>
      <div class="text-white/60" mt-50 mt-2 f-c-c gap-4>
        <div onclick="window.open('https://beian.miit.gov.cn/')">冀 ICP 备 2024088134 号</div>
        <div>© 2024 陈文生</div>
      </div>
    </footer>
  </main>

  <!-- 背景 -->
  <div id="background" absolute wh-full left-0 top-0 z-0>
    <!-- 渐变阴影 -->
    <div to-black-500 absolute h-80vh w-full bottom--30vh left-0 from-black bg-gradient-to-t />
    <!-- 星轨背景 -->
    <StarTrails pb-45vh bg-black />
  </div>
</template>

<style lang="scss" scoped>
#background.fixed {
  position: fixed;
  top: -70%;
}
</style>
