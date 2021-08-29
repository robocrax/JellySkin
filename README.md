<div align="center">
  <h1>JellySkin</h1>
  <p>My version of prayag17's skin with additional customizations from other places</p>
  <h3>Use 67% or 70% zoom in web browser for better experience</h3>
  <h4>Note: To take full experience of this CSS on FireFox scroll down below to find the necessary settings.</h4>
</div>
<br>
<h3>How to use</h3>

To use the JellySkin theme copy the line below into "Dashboard -> General -> Custom CSS" and click save, it will apply immediately server-wide to all users on top of any theme they may be using. To remove the theme, clear the "Custom CSS" field and then click save. 

<b>NOTE: Theme may not work when using a reverse proxy due to Content-Security-Policy. See fix below.</b>
  
  
Merged theme from here, there and a few tweaks:
  
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

  
  /* PR already created so should be fixed in near future but just in case */
  .navMenuOption .navMenuOptionIcon {
    width: 1.3em;
  }
  .dashboardSection .sectionTitleTextButton>.material-icons {
      margin-left: .5em;
  }

  
  .cardText-secondary, .fieldDescription, .guide-programNameCaret, .listItem .secondary, .nowPlayingBarSecondaryText, .programSecondaryTitle, .secondaryText {
      pointer-events: none;
  }


  .layout-mobile .overflowPortraitCard, .layout-mobile .overflowSquareCard {
      width: 50% !important;
  }

  .layout-mobile #itemDetailPage .cardBox {
      margin: .5em;
  }
  .padded-right {
      padding-right: 0;   /* to overcome the slider occupying the space but sliders new-tech so minimal */
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
```
