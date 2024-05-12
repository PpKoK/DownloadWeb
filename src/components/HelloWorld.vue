<template>
	<div id="building">
  <div class="container" :class="{ 'dark-mode': darkMode }">
    <div class="header">
      <div class="logo">PPGS</div>
      <div class="navbar">
        <a href="#">公告：开源MVVM前端JavaScript框架</a>
      </div>
      <div class="theme-toggle">
        <input type="checkbox" id="darkModeSwitch" :checked="darkMode" @change="toggleTheme">
        <label for="darkModeSwitch" class="toggle-label"></label>
      </div>
    </div>
    <div class="content">
      <div class="categories">
        <div v-for="(category, index) in categories" :key="index" class="category">
          <img :src="category.image" :alt="category.name + ' Image'" class="category-image">
          <span class="category-name" @click="selectCategory(index)" :class="{ 'active': selectedCategory === index }">{{ category.name }}</span>
        </div>
      </div>
      <div class="items">
        <div v-for="item in displayedItems" :key="item.id" class="item">
          <span class="title">{{ item.title }}</span>
          <div v-if="selectedCategory !== 0" class="downloads">
            <button @click="download(item.id, 1)">阿里云盘</button>
            <button @click="download(item.id, 2)">夸克网盘</button>
            <button @click="download(item.id, 3)">百度网盘</button>
          </div>
        </div>
      </div>
      
    </div>
	
  </div>
  <div class="pagination">
    <button class="pagination-button" @click="prevPage" :disabled="currentPage === 1">上一页</button>
    <span>第{{ currentPage }}页</span>
    <button class="pagination-button" @click="nextPage" :disabled="currentPage === totalPage">下一页</button>
  </div>
   </div>
   <div><footer class="footer"><p><a href="https://www.ppkok.com" class="creator-link">By:TANKS.www.ppkok.com</a>    
    Mail:ppkok2#icloud.com</p></footer></div>		   
   <div class="content">
           <div class="side-content">
             <div class="image-container">
               <img src="/img/qrcode.jpg" alt="Image Description">
             </div>
             <div class="text-container">
               <p>扫一扫关注公众号</p>
               <p>就不迷路了哦</p>
             </div>
           </div> </div>
</template>

<script>
export default {
  data() {
    return {
      selectedCategory: 0,
      categories: [
        {
          name: '首页',
          image: 'https://www.ppkok.com/upload/logo.webp',
          items: [
            { id: 1, title: '说明文档Vue.js是一个用于创建用户界面的开源MVVM前端JavaScript框架<br>也是一个创建单页应用的Web应用框架。Vue.js由尤雨溪创建，由他和其他活跃的核心团队成员维护。2016年一项针对JavaScript框架的调查表明，Vue有着89%的开发者满意度。在GitHub上，该项目平均每天能收获95颗星，为GitHub有史以来星标数第3多的项目。', downloadUrls: [] }
          ]
        },
        {
          name: 'Photoshop',
          image: './img/photoshop.svg',
          items: [ /* downloadUrls:1.阿里云盘2.夸克网盘3.百度网盘 */
            { id: 1, title: 'Ps2019 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 2, title: 'Ps2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] }
          ]
        },{
          name: 'Illustrator',
          image: './img/illustrator.svg',
          items: [
            { id: 3, title: 'Ai2021 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] },
            { id: 4, title: 'Ai2020 win 版', downloadUrls: ['https://www.ppkok.com', 'https://www.ppkok.com', 'https://www.ppkok.com'] }
          ]
        },
        // 其他分类...
      ],
      darkMode: false,
      searchTerm: '',
      currentPage: 1,
      itemsPerPage: 10
    };
  },
  computed: {
    filteredItems() {
      if (this.selectedCategory === null || !this.categories[this.selectedCategory]) {
        return [];
      }
      if (!this.searchTerm) {
        return this.categories[this.selectedCategory].items;
      }
      return this.categories[this.selectedCategory].items.filter(item =>
        item.title.toLowerCase().includes(this.searchTerm.toLowerCase())
      );
    },
    totalPage() {
      return Math.ceil(this.filteredItems.length / this.itemsPerPage);
    },
    displayedItems() {
      const startIndex = (this.currentPage - 1) * this.itemsPerPage;
      const endIndex = this.currentPage * this.itemsPerPage;
      return this.filteredItems.slice(startIndex, endIndex);
    }
  },
  methods: {
    selectCategory(index) {
      this.selectedCategory = this.selectedCategory === index ? null : index;
      this.currentPage = 1; // 自动跳转到第一页
    },
    download(itemId, downloadIndex) {
      const item = this.categories[this.selectedCategory].items.find(i => i.id === itemId);
      const downloadUrl = item.downloadUrls[downloadIndex - 1];
      window.location.href = downloadUrl;
    },
    toggleTheme() {
      this.darkMode = !this.darkMode;
      document.body.classList.toggle('dark-mode', this.darkMode);
    },
    search() {
      console.log('搜索内容:', this.searchTerm);
    },
    nextPage() {
      if (this.currentPage < this.totalPage) {
        this.currentPage++;
      }
    },
    prevPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    }
  }
};
</script>

<style scoped>

.container {
  width: 800px;
  margin: 0 auto;
}
.creator-link {
  text-decoration: none; 
  color: inherit; 
  }
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  border-bottom: 1px solid #ccc;
  margin-top: 10px;
}v

.logo a {
  font-size: 19px;
  font-weight: bold;
}

.navbar a {
  text-decoration: none;
  color: #333;
  margin-left: 10px;
}

.search-box {
  display: flex;
  align-items: center;
}

.search-input {
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 3px;
  margin-right: 5px;
  font-size: 14px;
}

.search-button {
  padding: 5px 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  font-size: 14px;
}

.theme-toggle {
  position: relative;
  display: inline-block;
  width: 40px;
  height: 20px;
}

.toggle-label {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #ccc;
  border-radius: 10px;
  cursor: pointer;
}

.toggle-label::after {
  content: '';
  position: absolute;
  top: 2px;
  left: 2px;
  width: 16px;
  height: 16px;
  background-color: #fff;
  border-radius: 50%;
  transition: transform 0.3s;
}

#darkModeSwitch:checked + .toggle-label::after {
  transform: translateX(20px);
}

.content {
  display: flex;
}

.categories {
  flex: 0 0 200px;
  padding: 20px;
}

.category {
  display: flex;
  align-items: center;
}

.category-image {
  width: 20px;
  height: 20px;
  margin-right: 20px;
}

.category-name {
  font-size: 22px; /* 与文字一样大 */
  margin-left: 1px; /* 图片在文字前面 1px */
}

.items {
  flex: 1;
  padding: 20px;
}

.item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid #ccc;
}

.title {
  flex: 1;
  margin-right: 10px;
}

.downloads button {
  padding: 5px 10px;
  background-color: #333333;
  color: #ffffff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  font-size: 14px;
  
}

.downloads button:not(:last-child) {
  margin-right: 5px;
}

.downloads button:hover {
  background-color: #0056b3;
}



.dark-mode .header,
.dark-mode .navbar a,
.dark-mode .search-box,
.dark-mode .theme-toggle,
.dark-mode .categories,
.dark-mode #building,
.dark-mode .text-container p,
.dark-mode .footer,
.dark-mode .items {
  background-color: #333333;
  color: #ffffff;
}
.dark-mode .downloads button
{
  background-color: #ffffff;
  color: #333333;
  }
.dark-mode body {
  background-color: #333333;
  color: #ffffff;
}

.side-content {
  position: fixed;
  top: 50%; 
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.image-container {
  width: 150px; 
  height: 150px; 
  overflow: hidden; 
}

.image-container img {
  width: 100%; 
  height: 100%; 
  object-fit: cover; 
}

.text-container {
  text-align: center;
  margin-top: 10px; 
}

.text-container p {
  margin: 0;
  font-size: 14px; 
  line-height: 1.5; 
}
.footer {
  text-align: center;
  background-color: #ffffff; /* 背景颜色 */
  padding: 5px 0; /* 上下内边距 */
  position: fixed; /* 固定在底部 */
  left: 0;
  bottom: 0;
  width: 100%; /* 宽度100% */
  font-size: 15px;
}
.pagination {
  text-align: center;
  margin-top: 20px;
}

.pagination-button {
  padding: 5px 10px;
  background-color: transparent; /* 透明背景 */
  border: none; /* 无边框 */
  cursor: pointer;
  font-size: 14px;
}

.pagination-button:disabled {
  cursor: not-allowed;
  color: #999999; /* 禁用状态文字颜色 */
}

  
</style>