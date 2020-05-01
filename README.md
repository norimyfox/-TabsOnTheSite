# TabsOnTheSite
Script example for tabs on the site.

We get elements with html:

````
let tab = document.querySelectorAll('.info-header-tab'), //Tab Switch Buttons
        info = document.querySelector('.info-header'), //Tab Parent
        tabContent = document.querySelectorAll('.info-tabcontent'); //Tabs that will switch
````

**You should get the tab switching buttons, their parent and the tabs that will switch**

We hide tabs that we do not need at the moment ***(in our case, everything except the first)***:

````
function hideTabContent(a) {
        for (let i = a; i < tabContent.length; i++) {
            tabContent[i].classList.remove('show'); // Removes the "show" class
            tabContent[i].classList.add('hide'); // Adds a "hide" to hide the tab on the page
        }
    }
    hideTabContent(1); // The arguments indicate the number of the tab that we need to display by default
````

Script to switch content:

````
function showTabContent(b) {
        if (tabContent[b].classList.contains('hide')) { //Checks whether the specified class has a slide and returns a boolean value
            tabContent[b].classList.remove('hide'); // Remove the "hide"
            tabContent[b].classList.add('show'); // Adds a show class so that the tab appears on the page
        }
    }
````

We attach the parent click event for the tab switching buttons:

````
info.addEventListener('click', function(event) {
        let target = event.target; //A new variable that is equal to our click target
        if (target && target.classList.contains('info-header-tab')) { //Check if our target is a toggle button
            for(let i = 0; i < tab.length; i++) { //Cycle
                if (target == tab[i]) { 
                    hideTabContent(0);
                    showTabContent(i);
                    break;
                }
            }
        }

    });
````
