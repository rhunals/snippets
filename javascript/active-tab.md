### HTML markup
```html
<div class="tabs">
  <a href="#" class="btn btn-primary settings-tab" id="updateProfile">Update Profile</a>
  <a href="#" class="btn btn-primary settings-tab" id="accountSetting">Account Settings</a>
  <a href="#" class="btn btn-primary settings-tab" id="bootcampSetting">Bootcamp Settings</a>
</div>
```

### Jquery script
```javascript
$(document).ready(function () {
  /*
    Make settings tab active after page reload
  */
  $('.settings-tab').click(function (e) {
    e.preventDefault();
    $('.settings-tab').removeClass('active');
    var current_tab = $(this).attr('id');
    $('#' + current_tab).addClass('active');
    setActiveTab(current_tab);
  });

  function setActiveTab(current_tab) {
    if (typeof (Storage) !== "undefined") {
      localStorage.setItem("activeTab", current_tab);
    } else {
      console.log('Sorry, Your browser does not support local storage.');
    }
  }

  function makeTabActive() {
    var storedTab = localStorage.getItem("activeTab");
    $('#' + storedTab).addClass('active');
  }

  // On page load set previously active tab
  makeTabActive();
 });
```
