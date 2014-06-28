CloudFoundry PHP Build pack を cakephpに対応した版です

CloudFoundry PHP Build packのDocumentRootがhtdocs(/home/vcap/app/htdocs/)
なので
htdocs/app/webroot
にするように
defaults/config/httpd/2.4.x/httpd.conf内を
--
#DocumentRoot "${HOME}/htdocs"
DocumentRoot "${HOME}/htdocs/app/webroot"
--
と書き換えただけです

ただ、これだけだとどうもうまくいかないので
cakephpのrootにあるindex.phpを
--
 -         define('CAKE_CORE_INCLUDE_PATH', ROOT . DS . 'lib');
 +         define('CAKE_CORE_INCLUDE_PATH', ROOT . DS . '../lib');
--
と書き換えてあげてください


本当はcf-exを作るべきなんでしょうね

