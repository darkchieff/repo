// ==UserScript==
// @name         Device Spoof UserAgent
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Spoofs the User-Agent to a mobile device for client-side detection.
// @author       You
// @match        *://*/*
// @grant        none
// @run-at       document-start // IMPORTANT: Run as early as possible
// ==/UserScript==

(function() {
    'use strict';

    // Set the desired User-Agent string for a device (e.g., Android phone on Chrome)
    const spoofedUserAgent = "Mozilla/5.0 (Linux; Android 10; K) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"; 

    // Override the native User-Agent property
    if (Object.defineProperty) {
        Object.defineProperty(navigator, 'userAgent', {
            get: function () {
                return spoofedUserAgent;
            }
        });
    } else if (Object.prototype.__defineGetter__) {
        navigator.__defineGetter__('userAgent', function () {
            return spoofedUserAgent;
        });
    }

    // You might also need to spoof other properties for better device disguise:
    Object.defineProperty(navigator, 'platform', {
        get: function () {
            return 'Android';
        }
    });
    
    // Spoofing maxTouchPoints to suggest a touch-enabled device
    Object.defineProperty(navigator, 'maxTouchPoints', {
        get: function () {
            return 5; // A value > 0 suggests touch capability
        }
    });

    console.log(`User-Agent spoofed to: ${navigator.userAgent}`);
})();
