FROM debian:sid

ADD birdie.deb /birdie.deb
RUN apt-get update && apt-get install -y libatk1.0-0 libcairo-gobject2 libcairo2 libcanberra0 libgdk-pixbuf2.0-0 libgee2 libglib2.0-0 libgtk-3-0 libgtksourceview-3.0-1 libjavascriptcoregtk-3.0-0 libnotify4 libpurple0 libwebkitgtk-3.0-0 xdg-utils desktop-file-utils libglib2.0-dev && rm -fr /var/lib/apt/lists/* && dpkg -i /birdie.deb

CMD "birdie"

