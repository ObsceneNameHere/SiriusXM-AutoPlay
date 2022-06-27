// ==UserScript==
// @name           SiriusXM Auto Play
// @license        GNU GPLv3
// @description    Auto plays music on page load, checks & clears idle checks then refreshes page.
// @match          http*://player.siriusxm.com/*
// @version        2.1.3
// @grant          GM_getValue
// @grant          GM_setValue
// @namespace https://greasyfork.org/en/scripts/411977-siriusxm-player-continuous-play
// ==/UserScript==


/* defines play/pause button */
const pB1=document.getElementsByClassName("play-pause-btn");
/* defines play/pause button status */
let pB2='';
/* defines page load state */
let rS1='';
/* defines inactivity timeout keep listening button */
const pU1=document.getElementsByClassName("modal-button-1");
/* defines another pointless pop up 'Hope you are enjoying siriusXM' */
const pU2=document.getElementsByClassName("overlay-button-1");
/*defines times an attempt to play has occurred*/
let rTcnt=0;



setTimeout(init1,5*1000)

function init1()
{
    rS1=document.readyState.toString();
    if (rS1 === 'complete')
    {
    pB2=document.getElementsByClassName('play-pause-btn').item('title').getAttribute('title').toString();
        cPlay();
    }
    else
    {
        setTimeout(init1,5*1000);
    }
}
function cPlay()
{
    pB2=document.getElementsByClassName('play-pause-btn').item('title').getAttribute('title').toString();
	if (pB2 === 'Play')
	{
        try
        {
            pB1[0].click();
            pCheck();
        }
        catch(err)
        {
            console.log('caught the error');
            console.log(err.message);
            setTimeout(init1,30*1000);
        }
	}
    if (pB2 === 'Pause')
     {
         pCheck();
     }
    else
    {
        setTimeout(init1,5*1000);
    }
}
function pCheck()
{
    pB2=document.getElementsByClassName('play-pause-btn').item('title').getAttribute('title').toString();

    if (pU1.length > 0)
    {
        pU1[0].click();
        wReload();
    }
    if (pU2.length > 0)
    {
        pU2[0].click();
        wReload();
    }
    if (pB2 === 'Play')
    {
        rTry();
    }
    else
    {
        setTimeout(pCheck,10*1000);
    }
}
function rTry()
{
    rTcnt += 1;
    if (rTcnt > 50)
    {
        rTcnt=0;
        wReload();
    }
    else
    {
        pB2=document.getElementsByClassName('play-pause-btn').item('title').getAttribute('title').toString();
        setTimeout(cPlay,10*1000);
    }
}

function wReload()
{
    setTimeout(() => {
        location.reload();
    }, 10*1000)
}
