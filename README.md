GSpace Overview
OKSpin - Gamify Your Brand
Easily Build private user engagement space，and Discover New value together.
1. GSpace Roundup
(1). About OKSpin GSpace
This platform is all about helping developers get closer to their users,Making users into players.Through a diverse ecosystem of interactive games, mission systems, competitive rankings, invitations to share and more, Let users enjoy it while safeguarding their privacy, Discover New value together.
(2). Privacy Policy
https://okspin.tech/privacy.html
(3). Docking process

When you see this document, you should be in step 2 or 3
2. Information preparation
On This platform page, you should create a developer account and add App(s) to get the AppKey, create Placement(s) and get the ID (as shown below).
App Key: Each App/Website will correspond to a unique AppKey, which is used to display and verify the access content.

Placement Id: Under each App,Placement will have a unique ID, you need to use the ID to display the content you access

3. SDK Integration
(1). Add SDK to your Project (build.gradle)
repositories{
    maven {
        url 'https://dl.gamifyspace.com/gamify/'
    }
}
dependencies {
    implementation 'com.gamify:space:3.0.4'
}

(2). Set Listener and Implement the Callbacks before SDK init
Gamify.setListener(new Gamify.GamifyListener() {

    @Override
    public void onInitSuccess() {
        // Invoked when SDK init success
    }

    @Override
    public void onInitFailed(GamifyError error) {
        // Invoked when SDK init failed
    }

    @Override
    public void onIconReady(String placement) {
        // Placement load success
    }

    @Override
    public void onIconLoadFailed(String placement, GamifyError error) {
        // Placement load failed
    }

    @Override
    public void onIconShowFailed(String placementId, GamifyError error) {
        // Placement show failed
    }

    @Override
    public void onIconClick(String placement) {
        // Invoked when user click Placement
    }

    @Override
    public void onInteractiveOpen(String placement) {
        // Invoked when GSpace - Interactive Ads page opened
    }

    @Override
    public void onInteractiveOpenFailed(String placementId, GamifyError error) {
        // Invoked when GSpace - Interactive Ads page open failed
    }

    @Override
    public void onInteractiveClose(String placement) {
        // Invoked when GSpace - Interactive Ads page closed
    }

    @Override
    public void onOfferWallOpen(String placementId) {
        // Invoked when GSpace - Interactive Wall page opened
    }

    @Override
    public void onOfferWallOpenFailed(String placementId, GamifyError error) {
        // Invoked when GSpace - Interactive Wall page open failed
    }

    @Override
    public void onOfferWallClose(String placementId) {
        // Invoked when GSpace - Interactive Wall page closed
    }

    @Override
    public void onGSpaceOpen(String placementId) {
        // Invoked when GSpace opened
    }

    @Override
    public void onGSpaceOpenFailed(String placementId, GamifyError error) {
        // Invoked when GSpace open failed
    }

    @Override
    public void onGSpaceClose(String placementId) {
        // Invoked when GSpace closed
    }

    /**
     * User interaction behavior callback
     * INTERACTIVE_PLAY         User play in GSpace - Interactive Ads
     * INTERACTIVE_CLICK        User click the gift in GSpace - Interactive Ads
     * OFFER_WALL_SHOW_DETAIL   Show offer details in GSpace - Interactive Wall
     * OFFER_WALL_GET_TASK      Get offer in GSpace - Interactive Wall
     */
    @Override
    public void onUserInteraction(String placementId, String interaction) {
    }
});

(3). Initialize
Gamify.initSDK("Your App Key");

(4). Placement Creative (Optional)
If you use a custom icon (The ad portal is created by yourself), please ignore this step.
a. Load Placement Creative
Gamify.loadIcon("Your Icon PlacementId");

b. Placement Creative Availability
if (Gamify.isIconReady("Your PlacementId")) {
    //Use Icon
}

c. Show Placement Creative
Once you receive the onIconReady callback, you can add Icon to the screen.After the display is successful, click the entry material to directly enter the placement page.
Note: You should call loadIcon before show it.
LinearLayout mLinearLayout = "{your Layout}";
View iconView = Gamify.showIcon("Your Icon PlacementId");
if (iconView != null) {
    if (iconView.getParent() != null) {
        ViewGroup viewGroup = (ViewGroup) iconView.getParent();
        viewGroup.removeView(iconView);
    }
    iconView.setLayoutParams(new ViewGroup.LayoutParams("IconWidth", "IconHeight"));
    mLinearLayout.addView(iconView);
}

4. Custom UserId
The Custom User ID is a parameter that GSpace must pass. It is used to call back relevant information to the developer when users redeem prizes or complete tasks in GSpace to determine the uniqueness of the user.
(1). Set Custom UserId
// Maximum length is 64 characters
Gamify.setUserId("Your Custom UserId");

(2). Get Custom UserId
String userId = Gamify.getUserId();

5. GSpace
You have successfully introduced the SDK into your project, and the next step is to access GSpace. You can find further examples on the Quickstart page for GSpace.
6. Other methods
Debug Mode
Gamify.debug(true);

