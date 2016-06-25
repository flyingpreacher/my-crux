Adding A Scrollbar To XTerm<br>
http://beforewisdom.com/blog/tech/xterm-with-a-scrollbar/


Bring up a terminal and sign in as root ( Ubuntu users can do this with sudo bash )

Install xorg-xrdb

Go to /usr/etc/X11/app-defaults (use 'locate app-defaults' to find where this file is on Crux)

    /usr/lib/X11/app-defaults

Bring up the file XTerm in a text editor

Copy the snippet below to the bottom of the file & save the file:

execute the command: xrdb -merge /etc/X11/app-defaults
    
    
	! Set up scrollbars - get them, get them on the right side, and be
	! able to scroll them with the right,left, or middle mouse button
	xterm*ScrollBar: on
	*XTerm*scrollBar: true
	xterm*rightScrollBar: true
	xterm*multiScroll: on
	xterm*jumpScroll: on
 
	xterm*scrollbar.Translations: #override \n\
  	:StartScroll(Continous) MoveThumb() NotifyThumb()\n\
  	:MoveThumb() NotifyThumb() \n\
  	:StartScroll(Continous) MoveThumb() NotifyThumb()\n\
  	:MoveThumb() NotifyThumb() \n\
  	:StartScroll(Continous) MoveThumb() NotifyThumb()\n\
  	:MoveThumb() NotifyThumb() \n\
  	:NotifyScroll(Proportional) EndScroll()

Then do this command:

    xrdb -merge /etc/X11/app-defaults/XTerm
    
This is needed to get the line to complete successfully.
