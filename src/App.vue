<template>
    <div id="app" class="dialog-wrapper">
        <svg viewBox="0 0 100 100" width="150" height="150" class="ballanim">
            <g transform="translate(50 50) scale(0.8)">
                <g transform="translate(0 50)">
                    <g class="gravity">
                        <g transform="translate(0 -50)">
                            <g class="ball" transform="scale(1 1)">
                                <g class="bottom">
                                    <path
                                        fill="#ffffff"
                                        stroke="#303030"
                                        stroke-width="5"
                                        d="M -47.5 0 a 47.5 47.5 0 0 0 95 0z"
                                    ></path>
                                </g>
                                <g class="top">
                                    <path fill="#f15d5f" d="M -47.5 0 a 47.5 47.5 0 0 1 95 0"></path>
                                    <path
                                        fill="none"
                                        stroke="#ffffff"
                                        stroke-width="5"
                                        stroke-linecap="round"
                                        stroke-dasharray="0 15 9 9 20 100"
                                        d="M -38 -0 a 38 38 0 0 1 76 0"
                                    ></path>
                                    <path
                                        fill="none"
                                        stroke="#303030"
                                        stroke-width="5"
                                        d="M -47.5 0 a 47.5 47.5 0 0 1 95 0z"
                                    ></path>
                                </g>
                                <g class="open" transform="scale(1 0)">
                                    <path
                                        fill="#303030"
                                        stroke="#303030"
                                        stroke-width="5"
                                        stroke-linejoin="round"
                                        d="M -47.5 -10 a 190 190 0 0 1 95 0 a 190 190 0 0 1 -95 0"
                                    ></path>
                                    <path
                                        fill="#303030"
                                        stroke="#303030"
                                        stroke-width="5"
                                        stroke-linejoin="round"
                                        d="M -47.5 5 a 160 160 0 0 0 95 0 a 180 180 0 0 0 -95 0"
                                    ></path>
                                </g>
                                <g class="center">
                                    <circle
                                        fill="#ffffff"
                                        stroke="#303030"
                                        stroke-width="5"
                                        cx="0"
                                        cy="0"
                                        r="12"
                                    ></circle>
                                    <circle
                                        fill="#ffffff"
                                        stroke="#303030"
                                        stroke-width="3"
                                        cx="0"
                                        cy="0"
                                        r="6"
                                    ></circle>
                                    <g class="inner" opacity="0">
                                        <circle fill="#f15d5f" cx="0" cy="0" r="4.5"></circle>
                                    </g>
                                </g>
                            </g>
                        </g>
                    </g>
                </g>
            </g>
        </svg>
        <div class="dialog-box">
            <p class="dialog-text">{{ displayedText }}</p>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const message = ref(`안녕하세여 소이김규가님들!

짧은 시간이었지만 저한테는 굉장히 즐거운 회사생활이었습니다!
3년동안 이런저런 굴곡도 있었지만 경학님덕분에 이렇게 좋은 인연을 만나기도 해서 좋네여
역시 사람은 케이티~

별건 아니구 추억겸 나름대로 실용적인 선물을 골라봤으니, 받으시고 도움이 되었으면 좋겠네여 ㅎㅎ

정보) 색깔이나 디자인이 투박해보여도 써보시면 짱좋은 마우스패드입니당
아무래도 저도 10년동안 쓰고있져?

연말 잘 보내시구, 앞으로도 멋진 선배님들이 되셨으면 좋겠습니다 ㅎㅎ

`);
const displayedText = ref("");
const typingSpeed = 100; // 타이핑 속도(ms)

const typeText = () => {
    let index = 0;
    const typingInterval = setInterval(() => {
        displayedText.value += message.value[index];
        index++;

        if (index === message.value.length) {
            clearInterval(typingInterval);
        }
    }, typingSpeed);
};

onMounted(() => {
    typeText();
});
</script>

<style>
/* 전체 레이아웃 */
.dialog-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: #f5f5dc; /* 포켓몬 느낌 배경 */
    font-family: "Press Start 2P", monospace;
}

/* 대화창 */
.dialog-box {
    width: 80%;
    max-width: 600px;
    background: #fff;
    border: 4px solid #000;
    border-radius: 8px;
    padding: 20px;
    box-shadow: 4px 4px 0 #000;
    text-align: left;
}

.dialog-text {
    font-size: 1rem;
    line-height: 1.5;
    white-space: pre-wrap;
    color: #000; /* 글씨 색상을 검정색으로 수정 */
}
</style>
