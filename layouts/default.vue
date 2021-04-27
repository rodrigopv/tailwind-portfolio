<template>
  <div class="flex flex-col min-h-screen min-w-screen w-screen h-screen">
    <div class="nav bg-white w-full md:w-2/5 lg:w-1/5 fixed flex content-center justify-center">
      <div class="flex logo justify-center content-center flex-col">
        <h1 class="p-3 font-bold text-lg pb-0">
          Tailwind Flexing<span class="inline-block text-3xl transform rotate-[-10deg]">💪</span>
        </h1>
        <h2 class="text-center flex items-center justify-center">
          <span class="mr-2">by</span>
          <a :href="'https://github.com/' + $config.githubUser" rel="_blank">
            <img class="rounded-full inline" :src="'https://github.com/' +  $config.githubUser + '.png'" width="24" height="24" >
            <span>{{ $config.githubUser }}</span>
          </a>
        </h2>
      </div>
    </div>
    <Nuxt />
  </div>
</template>

<style>
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
