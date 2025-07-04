<script lang="ts">
  import Navbar from '$lib/components/navigation/Navbar.svelte';
  import MinimumMarginImageSource from '$lib/widgets/MinimumMarginImageSource.svelte';
  import GeneratedImage from '$lib/widgets/GeneratedImage.svelte';
  import { SalemLogos } from '$lib/generated-images';

  // https://github.com/vitejs/vite/issues/14686
  // Importing the image in CSS directly does not invoke vite-imagetools.
  import Cloud9Slice from './cloud-9-slice.png';

  import SalemAnimated320 from './salem-animated-320.gif';
  import SalemSpritesheet322 from './salem-spritesheet-322.png';
  import DdrArrowSalem from './ddr-arrow-salem.gif';
  import { halfMainContentSizesList } from '$lib/layout/layout';
</script>

<picture>
  <!-- Require at least 200px on each side of the main content. -->
  <MinimumMarginImageSource doubleMinimumMarginExpr="400px" />
  <img
    src={DdrArrowSalem}
    alt=""
    class="decorative-arrow"
    width="120"
    height="116"
  />
</picture>

<div class="main-content">
  <Navbar>
    {#snippet logo()}
      <GeneratedImage
        image={SalemLogos}
        alt=""
        imgClass="fill-contain-left"
        sizes={halfMainContentSizesList}
      />
    {/snippet}
  </Navbar>

  <iframe
    class="salem-ps5-youtube-embed"
    src="https://www.youtube.com/embed/WRVonH0TTS8?si=KaPMz0EYsGnKOK9Z"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    referrerpolicy="strict-origin-when-cross-origin"
    allowfullscreen
  ></iframe>

  <p class="text-align-center">
    I created the fun and cute pixel art graphic effects for salem ilese's music
    video, PS5, in 2022. This was a super fun project and I had a lot of
    creative freedom to illustrate the bright, retro and playful MapleStory
    inspired GFX in this video. The assets are optimized for the potential to
    create a 2D platformer game in the future.
  </p>
  <p class="text-align-center">
    I worked with director Christina Xing and producer Laura Burhenn to create
    every instance of 2D animation in the final music video, with the approval
    of salem and the record label, Universal Music Group.
  </p>

  <img
    alt="spritesheet of an animation of salem ilese"
    src={SalemSpritesheet322}
    class="full-width-pixel-image"
  />

  <p
    class="margin-auto text-small indent-hanging cloud-9"
    style="--cloud-9-url: url('{Cloud9Slice}')"
  >
    Production Company: Our Secret Handshake<br />
    Director: Christina Xing<br />
    Producer: Laura Burhenn<br />
    Cinematographer: Justin McWilliams<br />
    1st AC: Walter Watkins<br />
    2nd AC/DIT: John Landry<br />
    Gaffer: Hiram Borges<br />
    Key Grip: Michael Roseman<br />
    First Lighting Tech: Joy Wang<br />
    Second Lighting Tech: Malik Dowdy<br />
    BBG: Taylor Reick<br />
    Grip: Andrew Soltay<br />
    1st AD: Jasmine Osean Thomas<br />
    Production Designer: Ava Jones<br />
    Set Decorators: Ethan Kankula & Daniel Richmond<br />
    Editor: Joan Pabon<br />
    Editorial Team: Digital Sword, Jack Melanson, Estefania Parra<br />
    Additional Editing: Neon Pig, Alex Familian, Anjoum Agrama<br />
    GFX: Reshma Zachariah<br />
    VFX: Ethan Madison<br />
    Color: Cameron Marygold<br />
    Line Producer: Erikx DiSantis<br />
    Production Coordinator: Brianna Liebling<br />
    PAs: Sydney Shelton, Aubrey Fowler, Rolando Rodas<br />
    BTS Photographer: Morgan Foitle<br />
    Director Rep: Jen Herrara for Las Bandas
  </p>

  <img
    alt="animated salem ilese sprite"
    src={SalemAnimated320}
    class="full-width-pixel-image"
  />
</div>

<style lang="scss">
  @use '$lib/layout/layout';

  .decorative-arrow {
    position: fixed;
    left: calc((100vw - layout.$main-content-width) / 2 - 140px);

    animation:
      6s linear 0s infinite decorative-arrow-falling,
      1s steps(5) 0s infinite alternate decorative-arrow-shaking;

    image-rendering: pixelated;
  }

  @keyframes decorative-arrow-falling {
    from {
      top: -116px;
    }
    to {
      top: 100%;
    }
  }

  .cloud-9 {
    border-image: var(--cloud-9-url) fill 100 / 600px repeat;
    padding: 80px;
    image-rendering: pixelated;
  }

  // For readability on mobile when lines wrap around.
  //
  // NOTE: Works in Firefox and Safari but not Chrome.
  .indent-hanging {
    text-indent: 3em hanging each-line;
  }

  .salem-ps5-youtube-embed {
    width: 100%;
    aspect-ratio: 560 / 315;
  }

  .margin-auto {
    margin: 0 auto;
  }

  .full-width-pixel-image {
    display: block;
    width: 100%;
    image-rendering: pixelated;
  }
</style>
