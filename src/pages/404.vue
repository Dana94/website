<template>
  <Layout>
    <div class="container-inner mx-auto py-16">
      <h2 class="text-4xl font-bold">
        Sorry, nothing but a blank
        <s>canvas</s> page here.
      </h2>
      <p class="text-2xl my-5">If you think something should be here, please <g-link to="/#contact">contact me</g-link>.</p>
      <g-link to="/">
        <button
          role="button"
          type="button"
          aria-label="Back to Home"
          class="block bg-purple-700 hover:bg-purple-800 text-white text-sm font-semibold tracking-wide uppercase shadow rounded cursor-pointer px-6 py-3 mb-4"
        >Back to Home</button>
      </g-link>
      <g-image src="../../static/undraw_blank_canvas.svg" alt="Woman looking at a blank canvas." />
    </div>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: "Page Not Found"
  }
};
</script>

