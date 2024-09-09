---
layout: page
title: Schedule
permalink: /schedule/
sort: 1
---


{% assign days = site.data.schedule | sort %}

<script>
function openTab(evt, tabName) {
  // Declare all variables
  var i, tabcontent, tablinks;

  // Get all elements with class="tabcontent" and hide them
  tabcontent = document.getElementsByClassName("tabcontent");
  for (i = 0; i < tabcontent.length; i++) {
    tabcontent[i].style.display = "none";
  }

  // Get all elements with class="tablinks" and remove the class "active"
  tablinks = document.getElementsByClassName("tablinks");
  for (i = 0; i < tablinks.length; i++) {
    tablinks[i].className = tablinks[i].className.replace(" active", "");
  }

  // Show the current tab, and add an "active" class to the button that opened the tab
  document.getElementById(tabName).style.display = "block";
  evt.currentTarget.className += " active";

  // Update the query string in the URL without reloading the page
  var newUrl = window.location.protocol + "//" + window.location.host + window.location.pathname + '?tab=' + tabName;
  window.history.pushState({ tab: tabName }, '', newUrl); // Push state with the tab name
}

// Helper function to activate a tab directly
function activateTab(tabName) {
  var i, tabcontent, tablinks;

  // Hide all tab content
  tabcontent = document.getElementsByClassName("tabcontent");
  for (i = 0; i < tabcontent.length; i++) {
    tabcontent[i].style.display = "none";
  }

  // Remove "active" class from all tab links
  tablinks = document.getElementsByClassName("tablinks");
  for (i = 0; i < tablinks.length; i++) {
    tablinks[i].className = tablinks[i].className.replace(" active", "");
  }

  // Show the target tab's content and mark the corresponding tab as active
  document.getElementById(tabName).style.display = "block";
  var tablink = document.querySelector('.tablinks[data-tab="' + tabName + '"]');
  if (tablink) {
    tablink.className += " active";
  }
}

// Restore the active tab based on the query string on page load
window.onload = function() {
  var urlParams = new URLSearchParams(window.location.search);
  var tabName = urlParams.get('tab');

  if (tabName && document.getElementById(tabName)) {
    // If a valid tab is specified in the query string, activate it
    activateTab(tabName);
  } else {
    // If no tab is specified, activate the first tab
    var firstTab = document.getElementsByClassName("tabcontent")[0].id;
    activateTab(firstTab);
  }
};

// Handle browser back/forward button navigation
window.onpopstate = function(event) {
  if (event.state && event.state.tab) {
    // Activate the tab stored in the history state object
    activateTab(event.state.tab);
  } else {
    // Fallback if no state is found (e.g., initial page load)
    var firstTab = document.getElementsByClassName("tabcontent")[0].id;
    activateTab(firstTab);
  }
};
</script>

<div class="tab">
{% for day in days %}
{% assign thisday = day[1] %}
  <button class="tablinks" data-tab="{{thisday.name}}" onclick="openTab(event, '{{thisday.name}}')">{{thisday.name}}</button>
{% endfor %}
</div>


{% for day in days %}
{% assign thisday = day[1] %}
{% include timeline.html day=thisday %}
{% endfor %}
