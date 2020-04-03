---
layout: notas
title: Nueva configuración de escritorio
---

<p style="text-align:justify">La situación actual volvió mandatorio el trabajo remoto. Esto, a su vez,
propició la necesidad de poner nuevamente a punto mi vieja notebook (una Acer Extensa 4620, que a la fecha
acusa más de 12 años ininterrumpidos de impecable servicio). Hacía algunos años que no la utilizaba en forma
intensiva <strong>en producción</strong>, por lo que mi entorno de escritorio acarreaba algunos vicios pendientes de resolución.
</p>

<p style="text-align:justify">La decisión más radical fue la de abandonar xorg, para pasarme por completo a <a href="https://wayland.freedesktop.org/">wayland</a>.
Aprovechando la disponibilidad de wayland en Archlinux, basé todo mi entorno preferentemente en aplicaciones
que soporten wayland en forma nativa. Una de las secuelas de esta decisión fue el abandono de xmonad. En la búsqueda
de un reemplazo equivalente, me encontré con <a href="https://swaywm.org/">Sway</a>. <br /> <br />

Los resultados hasta el momento han sido excelentes gracias a las siguientes herramientas:
</p>

* Wayland Compositor: <a href="https://swaywm.org/">Sway</a>
* Barra de estado: <a href="https://i3wm.org/i3status/manpage.html">i3status</a>.
* Editores de texto: <a href="https://howl.io/">howl</a>, <a href="https://www.vim.org/">vim</a>.
* Gestor de archivos: <a href="https://midnight-commander.org/">mc</a>, <a href="https://ranger.github.io/">ranger</a>.
* Visor de imágenes: <a href="https://github.com/eXeC64/imv">imv</a>.
* Emulador de terminal: <a href="https://terminator-gtk3.readthedocs.io/en/latest/">terminator</a>.

<p style="text-align:justify">Entre los cambios de configuración necesarios para que todo haya funcionado bien,
no quiero olvidar el siguiente:
</p>

{% highlight bash %}
#
# ~/.bash_profile
#

#Forzar apps GTK y firefox para que utilicen wayland en forma nativa
#(en lugar de XWayland).
export GDK_BACKEND=wayland
export CLUTTER_BACKEND=wayland
export MOZ_ENABLE_WAYLAND=1

#Utilizar Sway como compositor de wayland
if [[ -z $DISPLAY ]] && [[ $(tty) = /dev/tty1 ]]; then
  XKB_DEFAULT_LAYOUT=es exec sway
#
{% endhighlight %}

<br />

<p style="text-align:justify">Un vistazo de los resultados:</p>
<p align="center"><img src="/assets/img/20200403_16h32m07s_grim.png" height="400px" width="640px"></p>


