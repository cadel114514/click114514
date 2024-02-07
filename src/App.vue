<script setup lang="ts">
import { Ref, ref } from "vue";

let num: Ref<number> = ref(0);
let isHomo: boolean;
const sound: Ref<any> = ref();

function mainBtnClick(): void {
	num.value++;
	isHomo = [114, 1145, 11451].includes(num.value);
	//播放音效
	sound.value.play();
}

</script>

<template>
	<h1><span v-if="num != 114514">点到</span><span class="homoColor">114514</span></h1>
	<button id="mainBtn" :class="isHomo ? 'homoColor' : ''" v-if="num != 114514" @click="mainBtnClick">
		{{ num }}
	</button>
	<div v-else>
		<h1 class="homoColor">完全胜利</h1>
		<button id="re" @click="num = 0">重来</button>
	</div>

	<audio ref="sound">
		<source src="C:\Vue\my-vue-app\src\a114514.mp3">
	</audio>

	<br><br>
	<span>被按号：下北沢1145141919810</span>
</template>

<style>
.homoColor {
	color: saddlebrown;
}

#mainBtn {
	width: 300px;
	height: 300px;
	font-size: 70px;
	background-image: url("https://picx.zhimg.com/50/v2-21e4f33a31d1850f2efd4ff7375f061e_720w.webp?source=1def8aca");
	background-size: contain;
	border: 3px solid white;
	-webkit-text-stroke: 3px #000000;
	-moz-text-stroke: 3px #000000;
	font-weight: bold;
}

#mainBtn:hover {
	border: 3px solid saddlebrown;
}

#re {
	width: 100px;
	height: 35px;
}
</style>