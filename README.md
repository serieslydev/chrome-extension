# Tviso - Chrome extension addons

Public repository for tviso [Chrome extension](https://chrome.google.com/webstore/detail/tviso-extension/lmmeiimpckggkicjmjoldhpifoelbnfl) addons.

Tviso [Chrome extension](https://chrome.google.com/webstore/detail/tviso-extension/lmmeiimpckggkicjmjoldhpifoelbnfl) allows you to check movies, series and episodes from other sites with your [Tviso](https://www.tviso.com)'s user.

To add a new website into the extension, you have to create a new JavaScript file (you've got an example in the bottom of the page) and add a reference in the _sites.js file.

**Features**

* Tviso Chrome Extension injects jQuery to any compatible site, so you can use any selector or function
* If you want the raw code of the extension in order to test your addon, please contact us at [info@tviso.com](mailto://info@tviso.com). Otherise, you can create a pull request and we'll test and add it for you.


<pre><code>
/* global $ */
/* global document */
module.exports = function() {

    /**
     * Returns the type media type of the current page
     * @return {string} SERIE | MOVIE | EPISODE
     */
    var getMediaType = function() {
        return mediaType;
    };

    /**
     * Returns basic information of the current media
     * @param  {string} mediaType : received from "getMediaType" function
     * @return {object} 
     * 
     *  media {
     *      mediaType {string mandatory}: MOVIE | SERIE | EPISODE,
     *      title: {string mandatory} If mediaType is EPISODE, you should return the title of the serie
     *      imdb: {string optional} imdb id if exists (example "tt2389182")
     *      year: {int optional}
     *      cast: {string optional} a list of comma separed actors (example: "Scarlett Johansson,Morgan Freeman")
     *      director: {string optional} a list of comma separed directors
     *
     *      season: {int mandatory for EPISODE}: episode's season number
     *      episode: {int mandatory for EPISODE}: episode number
     *  }
     */
    var getMediaInfo = function(mediaType) {

        var media = {
            mediaType: mediaType,
            title: null,
            imdb: null,
            year: null,
            cast: [],
            directors: [],
            episode: null,
            season: null,
        };

        return media;
    };

    /**
     * The jQuery selectors of the page to interact with tviso
     * @return {object} with the format:
     *  {
     *      'jQuerySelector1': 'status1',
     *      'jQuerySelector2': 'status2'
     *  }
     * Status are: 'watched', 'following', 'pending' or 'no_status'
     */
    var checkSelectors = {
        return {

        }
    };

    return {
        name: '',   //A string identifier of the webpage
        url: '',    //A regexp to detect the page with the URL

        getMediaInfo: getMediaInfo,
        getMediaType: getMediaType,
        checkSelectors: checkSelectors
    };
};
</code></pre>