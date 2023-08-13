<script setup lang="ts">
import { Accordion } from "@/assets/animation/Accordion";

interface TimeLineData {
  time: string;
  title: string;
  contents: string[];
}

const attr = useAttrs();
const videoFood = ref<HTMLVideoElement>();
const videoShop = ref<HTMLVideoElement>();

const videoFoodTimeLine: TimeLineData[] = [
  {
    time: "0:00",
    title: "회원가입",
    contents: ["한글 아이디와 영어아이디 두개다 할수 있도록 만들었습니다."],
  },
  {
    time: "0:21",
    title: "로그인",
    contents: [],
  },
  {
    time: "0:27",
    title: "방만들기",
    contents: [
      "- 지도를 클릭 또는 주소찻기로 마크를 새길수 있습니다.",
      "- 주소찾기 는 다음 주소 찾기를 이용했습니다.",
    ],
  },
  {
    time: "0:44",
    title: "방찾기",
    contents: [
      "검색조건",
      "- All 은 모든방",
      "- 방이름은 포함될시 ",
      "- 방장은 일치할시",
    ],
  },
  {
    time: "1:08",
    title: "음식점 등록",
    contents: [],
  },
  {
    time: "2:02",
    title: "레스토랑 댓글 CRUD",
    contents: ["ws를 이용하여 실시간 변경을 확인할수 있게하였습니다."],
  },
  {
    time: "2:42",
    title: "레스토랑 찾기",
    contents: [],
  },
  {
    time: "3:19",
    title: "대기 신청 수락",
    contents: [
      "참여 수락할시알람api를 이용하여 알람을 알리고 클릭시 방에 주소로 접근할수 있게했습니다",
    ],
  },
  {
    time: "3:42",
    title: "내정보 수정",
    contents: [],
  },
  {
    time: "4:11",
    title: "회원 탈퇴",
    contents: [],
  },
];

const videoShopTimeLine: TimeLineData[] = [
  {
    time: "0:00",
    title: "회원가입",
    contents: ["- 고객 , 판매자 회원가입"],
  },
  {
    time: "0:40",
    title: "로그인",
    contents: ["- 봇 방지를 위한 reCAPTCHA를 사용했습니다."],
  },
  {
    time: "0:52",
    title: "물품 등록",
    contents: [
      "- 라우터 가드 기능을 넣어 페이지 이탈시 확인할수 있게하였습니다.",
      "- 상세설명 form은 toastui 라이브러리를 이용하였습니다.",
    ],
  },
  {
    time: "2:10",
    title: "물품 정보 변경",
    contents: [""],
  },
  {
    time: "2:31",
    title: "검색",
    contents: [""],
  },
  {
    time: "2:40",
    title: "장바구니 , 결제 , 구매 내역",
    contents: [
      "- 포트원(아임포트) 결제 모듈을 사용하여 결제환경을 구축하였습니다.",
    ],
  },
  {
    time: "3:43",
    title: "배송 상태 변경",
    contents: [
      "- Notification 활용하여 배송상태 변경을 알람으로 알수있습니다.",
    ],
  },
  {
    time: "4:12",
    title: "구매후기",
    contents: [""],
  },
  {
    time: "4:37",
    title: "문의",
    contents: [""],
  },
  {
    time: "5:26",
    title: "비밀번호 찾기",
    contents: [
      "nodeMailer 라이브러리를 활용한 임시 비밀번호를 메일로 받습니다.",
    ],
  },
  {
    time: "6:12",
    title: "OG META",
    contents: [
      "Open Graph태그를 이용하여 SNS,블로그 등 콘텐츠를 보여줄수있게 했습니다.",
    ],
  },
];

const setVideoTime = (ref: HTMLVideoElement, time: string) => {
  if (!ref) return;
  const [min, sec] = time.split(":");
  const moveTime = +min * 60 + +sec;

  ref.currentTime = moveTime;

  ref.scrollIntoView({ behavior: "smooth" });
};

onMounted(() => {
  const details = document.querySelectorAll("[data-details='Accordion']");

  details.forEach((el) => {
    new Accordion(el as HTMLElement);
  });
});
</script>

<template>
  <div :class="attr.class || ''">
    <!-- 포폴 1 -->
    <div
      class="flex flex-col gap-2 m-4 rounded-2xl bg-white sm:flex-row justify-between p-4"
    >
      <div class="w-full sm:w-[50%]">
        <!-- 영상 -->
        <div class="my-4">
          <video class="w-full px-2" ref="videoFood" controls>
            <source
              src="https://res.cloudinary.com/dhdq4v4ar/video/upload/v1675411794/foodreview_u2ifwz.mp4"
              type="video/mp4"
            />
          </video>
        </div>
        <!-- 타임라인 토글 -->
        <details data-details="Accordion">
          <summary>
            <span class="custom-marker">▶</span>
            <span>타임 라인</span>
          </summary>
          <!-- 타임 라인 -->
          <div class="content">
            <div class="w-full md:w-[35vw] flex-initial px-2">
              <h2 class="text-center text-[1.5rem] font-bold">타임라인</h2>

              <ol class="border-l border-gray-300">
                <li v-for="(item, index) in videoFoodTimeLine" :key="index">
                  <div class="flex flex-start items-center pt-3">
                    <div
                      class="bg-gray-300 w-2 h-2 rounded-full -ml-1 mr-3"
                    ></div>
                    <p
                      class="text-gray-500 text-sm cursor-pointer"
                      @click="setVideoTime(videoFood!, item.time)"
                    >
                      {{ item.time }}
                    </p>
                  </div>
                  <div class="mt-0.5 ml-4 mb-6">
                    <h4 class="text-gray-800 font-semibold text-xl mb-1.5">
                      {{ item.title }}
                    </h4>
                    <template v-if="item.contents.length > 0">
                      <p
                        class="text-gray-600 mb-3"
                        v-for="(content, ci) in item.contents"
                        :key="ci"
                      >
                        {{ content }}
                      </p>
                    </template>
                  </div>
                </li>
              </ol>
            </div>
          </div>
        </details>
      </div>
      <!-- content -->
      <div class="flex-1 font-[300]">
        <div class="my-2 flex gap-2 items-center">
          <a
            href="https://github.com/rlawncks125/pofol-foodreview"
            target="_blank"
            class="text-[2rem]"
          >
            <Icon name="bi:github" />
          </a>
          <a
            href="https://food.juchandev.xyz/"
            target="_blank"
            class="underline"
            >사이트</a
          >
        </div>
        <h1 class="text-[2.5rem]">오늘 밥은 뭐로먹을까</h1>
        <br />
        <h2 class="text-[1.5rem] font-bold">소개</h2>
        <div>
          <p>
            특정 집단(그룹)에 음식을 먹을시 개개인의 취향이 너무 달라서 메뉴를
            고르기에 어려움이 있습니다.
          </p>
          <p>
            웹 서칭을 하여 찾은 후기도 개개인의 후기이고 광고를 받아 좋은 말만
            적힌 광고 블로거 가 많았습니다.
          </p>
          <p>
            그래서 만들게 된
            <b class="text-pink-700">음식점 기록 서비스 </b>입니다.
          </p>
          <br />
          이 서비스에서 제공하는
          <b class="text-pink-700"> 주요 기능 </b>
          은 3가지 가 있습니다.
          <ul>
            <li>1. 마커 를 이용한 리뷰 중심지 결정</li>
            <li>2. 참여 승인/거부 로 개방적이지 않은 폐쇄적 방관리</li>
            <li>3. 폐쇄적인 관리로 인한 솔직한 기록</li>
          </ul>
        </div>
        <br />
        <div>
          <h2 class="text-[1.2rem] font-bold">구현 기술</h2>
          <ul>
            <li>- naverMaps API를 이용한 지도 기반 프로젝트 구성</li>
            <li>- REST API 를 이용한 회원 , 방 , 음식점 , 리뷰 CRUD 구성</li>
            <li>
              - Socket 으로 인한 실시간 데이터 변경 ( 댓글 변경 , 방정보 변경 )
              확인
            </li>
            <li>- ServiceWorker를 이용한 캐싱 , 알람 API ( 방 승인시 알람 )</li>
          </ul>
        </div>
        <br />
        <h2 class="text-[1.5rem] font-bold">사용 기술</h2>
        <div>
          <p>#FE : Vue.js , Tailwind.css</p>
          <p>#BE : Nest.js</p>
        </div>
      </div>
    </div>
    <hr />
    <!-- 포폴 2 -->
    <div
      class="flex flex-col gap-2 m-4 rounded-2xl bg-white sm:flex-row justify-between p-4"
    >
      <div class="w-full sm:w-[50%]">
        <!-- 영상 -->
        <div class="my-4">
          <video class="w-full px-2" ref="videoShop" controls>
            <source
              src="https://res.cloudinary.com/dhdq4v4ar/video/upload/v1676287371/nuxt-shop_lkx3qp.mp4"
              type="video/mp4"
            />
          </video>
        </div>
        <!-- 타임라인 토글 -->
        <details data-details="Accordion">
          <summary>
            <span class="custom-marker">▶</span>
            <span>타임 라인</span>
          </summary>
          <!-- 타임 라인 -->
          <div class="content">
            <div class="w-full md:w-[35vw] flex-initial px-2">
              <h2 class="text-center text-[1.5rem] font-bold">타임라인</h2>

              <ol class="border-l border-gray-300">
                <li v-for="(item, index) in videoShopTimeLine" :key="index">
                  <div class="flex flex-start items-center pt-3">
                    <div
                      class="bg-gray-300 w-2 h-2 rounded-full -ml-1 mr-3"
                    ></div>
                    <p
                      class="text-gray-500 text-sm cursor-pointer"
                      @click="setVideoTime(videoShop!, item.time)"
                    >
                      {{ item.time }}
                    </p>
                  </div>
                  <div class="mt-0.5 ml-4 mb-6">
                    <h4 class="text-gray-800 font-semibold text-xl mb-1.5">
                      {{ item.title }}
                    </h4>
                    <template v-if="item.contents.length > 0">
                      <p
                        class="text-gray-500 mb-3"
                        v-for="(content, ci) in item.contents"
                        :key="ci"
                      >
                        {{ content }}
                      </p>
                    </template>
                  </div>
                </li>
              </ol>
            </div>
          </div>
        </details>
      </div>
      <div class="flex-1 font-[300]">
        <div class="my-2 flex gap-2 items-center">
          <a
            href="https://github.com/rlawncks125/portfolio_Nuxt_Shopping"
            target="_blank"
            class="text-[2rem]"
          >
            <Icon name="bi:github" />
          </a>
          <a
            href="https://nuxt-shop.juchandev.xyz/"
            target="_blank"
            class="underline"
            >사이트</a
          >
        </div>
        <h1 class="text-[2.5rem]">쇼핑몰 하나는 있어야지</h1>
        <br />
        <h2 class="text-[1.5rem] font-bold">소개</h2>
        <div>
          검색엔진 최적화 ( SEO )가 강점인 SSR 렌더링 방식 으로 쇼핑몰을
          만들어봤습니다.
        </div>
        <br />
        <h2 class="text-[1.5rem] font-bold">주요기능</h2>
        <div>
          <ul>
            <li>- OG META</li>
            <li>- 동적 라우터 를 이용한 <b>미리 보기 화면</b> 생성</li>
            <li>
              - vue-router <b>네비게이션 가드</b> 를 이용하여 잘못된 페이지 이탈
              방어
            </li>
            <li>- 봇방지 를 위한 <b>reCAPTCHA</b>를 사용</li>
            <li>
              - <b>ServiceWorker</b>를 이용한 알람 API ( 물품 상태 변경시 알람 )
            </li>
            <li>- <b>웹 마스터 도구</b> 에 등록하여 <b>검색 엔진 노출</b></li>
          </ul>
        </div>
        <br />
        <h2 class="text-[1.5rem] font-bold">사용 기술</h2>
        <div>
          <p>#FE : Nuxt.js , Tailwind.css</p>
          <p>#BE : Nest.js</p>
        </div>
      </div>
    </div>
    <br />
  </div>
</template>

<style lang="scss">
details {
  border: 1px solid black;

  summary {
    padding: 0 0.5rem;
    cursor: pointer;
    & ~ .content {
      padding: 1rem;
      border-top: 1px solid black;
    }

    // 마커 없애기
    list-style: none;
    &::-webkit-details-marker {
      display: none;
    }

    .custom-marker {
      margin-right: 5px;
      float: left;
      clear: both;
      pointer-events: auto;
      transform: rotate(0deg);
      transition: transform 0.1s;
    }
  }

  &[open] summary {
    .custom-marker {
      transform: rotate(90deg);
    }
  }
}
</style>
