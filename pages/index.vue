<script setup lang="ts">
definePageMeta({
  layout: "active-link-page-scroll",
});
</script>

<template>
  <section>
    <div
      class="h-[20rem] flex justify-center items-center text-[2rem] text-center"
    >
      <Typer
        :text="['안녕하세요.', '주니어 개발자', '김주찬 입니다.']"
        :speed="100"
      />
    </div>
  </section>

  <ActiveLinkPageScrollSection
    class="p-4 text-center break-all mx-auto max-w-[800px]"
    bg-color="white"
    section-id="소개"
  >
    <div class="text-[1rem] font-[300]">
      <p>
        저는 새로운 도전과 학습을 즐기는 자기 주도적인 성향을 가지고 있습니다.
      </p>
      <p>
        어떤 분야에서든 호기심과 열정으로 스스로 공부하고 발전하기 위해
        노력합니다.
      </p>
      <p>
        프론트 엔드 개발 분야에서는 효율적이고 사용자 친화적인 웹 애플리케이션을
        개발하기 위해 다양한 기술과 도구를 습득하고 적용하는 데에 주력하고
        있습니다.
      </p>
      <p>
        저는 새로운 기술 동향과 트렌드에 관심이 많습니다. 업계의 변화에 민감하게
        대응하기 위해 지속적인 학습과 자기계발을 추구하고 있습니다. 
        <p>
          현재는 Vue.js와 Nuxt.js에 집중하고 있으나, React.js나 Angular 등 다른
          프레임워크도 익히고자 하는 욕심이 있습니다.
        </p>
      </p>
    </div>
  </ActiveLinkPageScrollSection>

  <!-- About -->
  <ActiveLinkPageScrollSection
    class="py-[4rem]"
    bg-color="#F9C51D"
    section-id="About"
  >
    <div class="max-w-dialogue mx-auto h-full">
      <div
        class="w-[80%] h-[80%] mx-auto grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10 items-center"
      >
        <div>
          <div class="flex gap-2 items-center">
            <Icon name="mdi:account" class="text-[3rem]" />
            <div class="flex flex-col gap-2">
              <p>이름</p>
              <span class="font-[300]">김주찬</span>
            </div>
          </div>
        </div>
        <div>
          <div class="flex gap-2 items-center">
            <Icon name="mdi:calendar-range" class="text-[3rem]" />
            <div class="flex flex-col gap-2">
              <p>생년 월일</p>
              <span class="font-[300]">97.07.03</span>
            </div>
          </div>
        </div>
        <div>
          <div class="flex gap-2 items-center">
            <Icon name="mdi:map-marker-check" class="text-[3rem]" />
            <div class="flex flex-col gap-2">
              <p>주소지</p>
              <span class="font-[300]">인천 광역시</span>
            </div>
          </div>
        </div>
        <div>
          <div class="flex gap-2 items-start">
            <Icon name="fluent:call-20-filled" class="text-[3rem]" />
            <div class="flex flex-col gap-2">
              <p>연락처</p>
              <span class="font-[300]">010-7115-9176</span>
            </div>
          </div>
        </div>
        <div>
          <div class="flex gap-2 items-start">
            <Icon name="material-symbols:mail" class="text-[3rem]" />
            <div class="flex flex-col gap-2">
              <p>이메일</p>
              <span class="font-[300] text-[0.8rem]"
                >rlawncks125@naver.com</span
              >
            </div>
          </div>
        </div>
        <div>
          <div class="flex gap-2 items-start">
            <Icon name="teenyicons:school-outline" class="text-[3rem]" />
            <div class="flex flex-col gap-2">
              <p>학력</p>
              <span class="font-[300]">고등학교 졸업</span>
            </div>
          </div>
        </div>
        <div>
          <div class="flex gap-2 items-start">
            <Icon name="entypo:v-card" class="text-[3rem]" />
            <div class="flex flex-col gap-2">
              <p>자격증</p>
              <ol class="list-decimal pl-[.8rem]">
                <li>정보처리 기사</li>
                <li>컴퓨터 활용 1급</li>
                <li>리눅스 마스터</li>
              </ol>
            </div>
          </div>
        </div>
      </div>
    </div>
  </ActiveLinkPageScrollSection>

  <!-- skill -->
  <ActiveLinkPageScrollSection bg-color="#ffbb99" section-id="Skill">
    <div class="h-[66rem] sm:h-[40rem] p-2 max-w-dialogue mx-auto">
      <p class="text-center text-[3rem] font-[700] my-[2rem]">Skills</p>
      <!-- skil warp -->
      <div
        class="grid grid-cols-1 sm:flex flex-col flex-wrap max-h-[80%] gap-3"
      >
        <!-- Front -->
        <div
          class="bg-[#ffbb99] p-4 border border-black rounded-xl shadow-lg shadow-current"
        >
          <h2 class="text-[3rem]">Front</h2>
          <!-- Front Wrap -->
          <div class="flex flex-col gap-2">
            <!-- HTML -->
            <div class="flex gap-2 items-center">
              <Icon class="text-[3rem]" name="skill-icons:html" />
              <span>HTML</span>
            </div>
            <!-- CSS -->
            <div class="flex gap-2 items-center">
              <Icon class="text-[3rem]" name="skill-icons:css" />
              <span>CSS</span>
            </div>
            <!-- JS -->
            <div class="flex gap-2 items-center">
              <Icon class="text-[3rem]" name="skill-icons:javascript" />
              <span>javaScript</span>
            </div>
            <!-- TS -->
            <div class="flex gap-2 items-center">
              <Icon class="text-[3rem]" name="skill-icons:typescript" />
              <span>typeScript</span>
            </div>
            <!-- vue.js -->
            <div class="flex gap-2 items-center">
              <Icon class="text-[3rem]" name="devicon:vuejs" />
              <span>Vue.js</span>
            </div>
            <!-- Nuxt.js -->
            <div class="flex gap-2 items-center">
              <Icon class="text-[3rem]" name="devicon:nuxtjs" />
              <span>Nuxt.js</span>
            </div>
          </div>
        </div>
        <!-- Backend -->
        <div
          class="bg-[#ffbb99] p-4 border border-black rounded-xl shadow-lg shadow-current"
        >
          <h2 class="text-[3rem]">Backend</h2>
          <!-- Backend Wrap -->
          <div class="flex flex-col gap-2">
            <div class="flex gap-2 items-center">
              <Icon class="text-[3rem]" name="logos:nestjs" />
              <span>Nest.js</span>
            </div>
          </div>
        </div>
        <!-- etc -->
        <div
          class="bg-[#ffbb99] p-4 border border-black rounded-xl shadow-lg shadow-current"
        >
          <h2 class="text-[3rem]">etc</h2>
          <!-- etc wrap -->
          <div class="flex flex-col gap-2">
            <div class="flex gap-2 items-center">
              <Icon class="text-[3rem]" name="devicon:docker" />
              <span>docker</span>
            </div>
            <div class="flex gap-2 items-center">
              <div class="flex">
                <Icon
                  class="text-[3rem] text-[#0277BD]"
                  name="teenyicons:windows-solid"
                />
                <Icon class="text-[3rem]" name="ic:baseline-plus" />
                <Icon class="text-[3rem]" name="flat-color-icons:linux" />
              </div>
            </div>
            <span>windows + 리눅스 ( wsl 2)</span>
          </div>
        </div>
      </div>
    </div>
  </ActiveLinkPageScrollSection>

  <!-- 프로젝트 -->
  <ActiveLinkPageScrollSection
    class=""
    bg-color="#ffa64d"
    section-id="프로젝트"
  >
    <h1 class="text-[3rem] text-center py-8">프로젝트</h1>
    <Projects class="max-w-dialogue mx-auto" />
    <!-- 배운점 -->
    <div class="px-4">
      <div class="max-w-dialogue mx-auto">
        <h2 class="text-center text-[3rem] py-[2rem]">배운점</h2>
        <!-- Front -->
        <div class="font-[300] bg-white rounded-lg p-4 my-2">
          <h2 class="text-[2.5rem] font-[700]">Front</h2>
          <!-- vue -->
          <div>
            <p class="text-[1.5rem] font-[700] text-green-600">Vue</p>
            <ul class="list-disc ml-4">
              <li>
                <b>상태 관리</b> 라이브러리( vuex , pinia )로 인한
                컴포넌트/페이지간에 상태공유 할수 있습니다.
              </li>
              <li>
                <b>컴포넌트 , 컴포저블</b> 을 통한 <b>캡슐화와 재사용</b> 할수
                있습니다.
              </li>
              <li>
                <b>MVVM 패턴</b> 으로 인한 <b>데이터 바인딩</b> 통해을 데이터를
                연결 하여 변경된 내용을 자동으로 반영 할수 있습니다.
              </li>
            </ul>
          </div>
          <!-- nuxt -->
          <p class="text-[1.5rem] font-[700] text-green-600">Nuxt</p>
          <ul class="list-disc ml-4">
            <li>
              Vue의 <b>서버사이드 프레임 워크</b>로 Vue와
              <b>같은 문법과 파일</b>을 통한 접근으로 쉽게 도입할수 있습니다.
            </li>
            <li>
              미리 설정된 개발 환경으로 <b>빠른 개발환경</b>을 구성할수
              있었습니다
            </li>
            <li>
              Vue 프로젝트 에서도 Nuxt와 같은 개발 환경을 구성 도입 할수 있음을
              알게 되었습니다.
            </li>
            <li>
              <b>파일 구조 가이드 라인</b>이 있어 파일구조를 고민하고 있던
              저에게 도음이 많이 되었습니다.
            </li>
            <li>
              SSR , SSG 등 서버 웹 서비스 방식과 웹마스터 도구와 SEO 를 통한
              <b>검색엔진 노출</b>하는 방법 을 배울수 있었습니다.
            </li>
          </ul>
          <!-- 기타 -->
          <p class="text-[1.5rem] font-[700] text-green-600">기타</p>
          <ul class="list-disc ml-4">
            <li>
              <b>외부 API</b> 를 사용하는 법을 배웠습니다.
              <p>ex) naverMaps , reCAPTCHA , 포트원 등등</p>
            </li>
            <li>
              <b>서비스 워커</b>를 통한 <b>PWA(웹 앱)</b> 개발과 리소스
              <b>캐싱</b>을 통한 웹 성능 개선과 <b>push 알람</b> 을 이용한
              알람을 보낼수 있었습니다.
            </li>
          </ul>
        </div>
        <!-- Backend -->
        <div class="font-[300] bg-white rounded-lg p-4 my-2">
          <h2 class="text-[2.5rem] font-[700]">Backend</h2>
          <!-- nest.js -->
          <div>
            <p class="text-[1.5rem] font-[700] text-red-800">Nest</p>
            <ul class="list-disc ml-4">
              <li>
                node.js 프레임워크로 Document를 읽으면서 서버를 개발하며 학습
                할수 있었습니다.
              </li>
              <li>
                백엔드를 직접 구축하며 FE 와 어떻게 통신 하는지 알수 있었습니다.
              </li>
              <li>데이터를 어떻게 처리하는지 알 수 있었습니다.</li>
              <li>
                프론트 단 에서 중요 데이터 관리시 보안이 취약하여 서버 단에서
                많은 처리를 해야하는 것을 알게되었습니다.
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <!-- 시행 착오 -->
    <!-- <div class="max-w-dialogue mx-auto px-4">
      <h2 class="text-center text-[3rem] py-[2rem]">시행착오</h2>
      #문제1
      <div class="bg-white rounded-lg p-4">
        <h2 class="text-[2.5rem] font-[700]">한글 아이디 깨짐</h2>
        <h3 class="text-[1.5rem]">[문제점]</h3>
        <p>서버에서 데이터를 받을때 아이디 문자열이 깨져서 들어옴</p>
        <h3 class="text-[1.5rem]">[ 해결 ]</h3>
        <p>
          한글 아이디를 base64 문자열 인코딩하여 서버로 보내고 서버 에서
          디코딩하여 해결
        </p>
      </div>
      #문제2
      <div class="bg-white rounded-lg p-4 my-2">
        <h2 class="text-[2.5rem] font-[700]">리전 문제</h2>
        <h3 class="text-[1.5rem]">[ 환경 ]</h3>
        <ul>
          <li>DB - 가비아 ( 한국 리전 )</li>
          <li>
            서버 배포 - <del class="line-through">Koyeb ( 미국 리전 )</del> →
            Cloudtype( 한국 리전 )
          </li>
          <li>FE 배포 - netlify ( 유럽 리전 )</li>
        </ul>
        <h3 class="text-[1.5rem]">[문제점]</h3>
        <ul class="list-disc ml-4">
          <li>
            Heroku의 무료 티어 종료로 인한 서버와 DB 배포 사이트를 변경하면서
            발생 하였다.
          </li>
          <li>
            서버 와 DB는 연결이 필요하기떄문에 리전이 멀리떨어져 버려 연결 시간
            대해 문제가 많이 발생하였다.
          </li>
          <li>
            이문제로 웹마스터도구( 수집 ) , typeORM( 타임 아웃 ) 문제가 생겼다.
          </li>
        </ul>
        <h3 class="text-[1.5rem]">[ 해결 ]</h3>
        <ul class="list-disc ml-4">
          <li>배포 사이트를 한국리전인 Cloudtype으로 변경</li>
          <li>
            추후 FE 배포도 Vercel ( 한국 리전 ) 으로 바꾸니 성능이 훨씬
            좋아졌다.
          </li>
        </ul>
      </div>
    </div> -->

    <br />
  </ActiveLinkPageScrollSection>

  <footer class="bg-[#334155] text-gray-200 p-4">
    Copyright 2023. 김주찬. all rights reserved.
  </footer>
</template>

<style lang="scss"></style>
