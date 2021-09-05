<div align="center">
  <h1>JellySkin</h1>
  <p>My version of <a href="https://github.com/prayag17/JellySkin">prayag17</a>'s skin with additional customizations from other places including <a href="https://github.com/CTalvio/Ultrachromic">CTalvio</a></p>
  <h3>Use 67% or 70% zoom in web browser for better experience</h3>
  <p>I personally don't see the need to zoom out that much as theme works great out of box, this is personal preference</p>
</div>
<br>
<h3>How to use</h3>

To use the JellySkin theme copy the line below into "Dashboard -> General -> Custom CSS" and click save, it will apply immediately server-wide to all users on top of any theme they may be using. To remove the theme, clear the "Custom CSS" field and then click save. 

<b>NOTE: Theme may not work when using a reverse proxy due to Content-Security-Policy. See fix below.</b>
  
  
<p>My compiled version. Merged main theme from here, another component there and a few tweaks:</p>
  
```css
  @import url("https://cdn.jsdelivr.net/gh/prayag17/JellySkin/default.css");
  @import url("https://cdn.jsdelivr.net/gh/prayag17/JellySkin/addons/Logo.css");

  
  @import url('https://cdn.jsdelivr.net/gh/CTalvio/Ultrachromic/overlayprogress.css');
  /* for OverlayProgress.css to overwrite JellySkin back to defaults */
  .innerCardFooter {
      height: 100%;
      width: auto;
      left: 0;
      transform: none;
      border-radius: revert;
  }
  .itemProgressBarForeground {
      background: linear-gradient(140deg, rgba(170, 92, 195, 0.4), rgba(0, 164, 220, 0.4)) !important;
  }
  #itemDetailPage .itemProgressBar, #indexPage .itemProgressBar {
      height: 100%;
  }


  .navMenuOption .navMenuOptionIcon,
  .listItemIcon.material-icons {
    width: 1em !important;
  }
  .dashboardSection .sectionTitleTextButton>.material-icons {
      margin-left: .5em;
  }

  
  .cardText-secondary, .fieldDescription, .guide-programNameCaret, .listItem .secondary, .nowPlayingBarSecondaryText, .programSecondaryTitle, .secondaryText {
      pointer-events: none;
  }


  .layout-mobile .vertical-wrap>.overflowPortraitCard, 
  .layout-mobile .vertical-wrap>.overflowSquareCard {
      width: 50% !important;
  }

  .layout-mobile #itemDetailPage .cardBox {
      margin: .5em;
  }
  .layout-mobile .detailPageWrapperContainer {
      width: 93%;
      margin: 20px auto 0;
  }
  .layout-mobile .detailPageContent {
      padding-bottom: 3rem;
  }
  .layout-mobile .detailPageWrapperContainer::after {
      width: 93%;
      height: calc(100% - 4em - 14px);
      bottom: 0px;
  }
  .layout-mobile .cardText>.textActionButton {
      color: #fff;
  }
  .layout-mobile #itemDetailPage .cardBox {
      background: #444 !important;
  }
  .layout-mobile #itemDetailPage .cardBox {
      box-shadow: 0px 0.1em 0.25em -0.1em #5d5d5d, 0px 0px 0.5em 0px #a1a1a1;
  }

  .layout-mobile .vertical-wrap > .overflowBackdropCard, 
  .layout-mobile .vertical-wrap > .overflowSmallBackdropCard {
      width: 100%;
  }


  /*  login tweaks mobile */
  .layout-mobile #loginPage .padded-left.padded-right.padded-bottom-page {
      margin-bottom: 1rem;
  }
  
  
  /* Realised My Media section is not first in my setup, uncomment this code to change yours (if yours isn't the first as well, default not required) *
  .section0 button.itemAction.textActionButton {
      height: auto;
  }
  .section3 button.itemAction.textActionButton {   /* apply to the 4th home section *
      height: 2em;
  } */
  
  
  
  /* Admin dashboard progress fix because of excessive use of !important 😂 */
  .transcodingProgress>.itemProgressBarForeground {
      background: #dd4919 !important;
  }
  .backgroundProgress>.itemProgressBarForeground {
      background: #303030 !important;
  }

  .padded-right-withalphapicker {
      padding-right: 3.5% !important;
  }
  .layout-mobile .detailPageWrapperContainer .itemsContainer.padded-right {
  	padding-right: 0 !important;
  }
  /* some content in dashboard got trimmed */
  .layout-mobile .dashboardDocument .listItemBodyText {
      max-width: none !important;
  }

  /* series Seasons horizonal scroller did not have the "seamless" effect */
  .layout-mobile #childrenContent .hiddenScrollX {
      -webkit-mask: linear-gradient(to left,transparent,black 15px calc(100% - 15px),transparent);
      mask: linear-gradient(to left,transparent,black 15px calc(100% - 15px),transparent);
      padding-left: 3.3%;
      padding-right: 3.3%;
  }
```

To fix theme not loading behind a reverse-proxy, add this **Content-Security-Policy** to your headers

```
default-src https: data: blob: http://image.tmdb.org; style-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net/gh/prayag17/JellySkin/ https://cdn.jsdelivr.net/gh/prayag17/JellySkin/addons/ https://cdn.jsdelivr.net/gh/prayag17/JellySkin/addons/Gradients/ https://cdn.jsdelivr.net/gh/prayag17/Jellyfin-Icons@latest/Font%20Awesome/ https://cdn.jsdelivr.net/gh/CTalvio/Ultrachromic/ https://pro.fontawesome.com/releases/v5.15.3/css/; script-src 'self' 'unsafe-inline' https://www.gstatic.com/cv/js/sender/v1/cast_sender.js https://www.youtube.com blob:; worker-src 'self' blob:; connect-src 'self'; object-src 'none'; frame-ancestors 'self'
```

I use Caddy 2 as my proxy so my config file would be:

```
jellyfin.domain.tld {
    header Content-Security-Policy "default-src https: data: blob: http://image.tmdb.org; style-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net/gh/prayag17/JellySkin/ https://cdn.jsdelivr.net/gh/prayag17/JellySkin/addons/ https://cdn.jsdelivr.net/gh/prayag17/JellySkin/addons/Gradients/ https://cdn.jsdelivr.net/gh/prayag17/Jellyfin-Icons@latest/Font%20Awesome/ https://cdn.jsdelivr.net/gh/CTalvio/Ultrachromic/ https://pro.fontawesome.com/releases/v5.15.3/css/; script-src 'self' 'unsafe-inline' https://www.gstatic.com/cv/js/sender/v1/cast_sender.js https://www.youtube.com blob:; worker-src 'self' blob:; connect-src 'self'; object-src 'none'; frame-ancestors 'self'"
    reverse_proxy localhost:8096
}
```
