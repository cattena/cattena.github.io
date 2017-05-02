---
layout: notas
title: Configuración Personalizada de XMonad
---

<p align="center"><img src="/assets/img/2017-05-01-205350_1280x800_scrot.png" height="400px" width="640px"></p>

<p style="text-align:justify">XMonad es uno de los mejores gestores de ventanas para GNU/Linux.
A partir de la versi&oacute;n 0.12, se requiere algo más de cuidado para que las
ventanas respeten el espacio de barra de estado, de tal forma que esta última quede siempre visible.
</p>

<p style="text-align:justify">A raíz de los cambios introducidos a partir de la mencionada versi&oacute;n,
he empezado a re-escribir por completo mi configuración, utilizando dzen2 para la barra de estado.
En el código fuente del módulo <a 
href="https://hackage.haskell.org/package/xmonad-contrib-0.13/docs/src/XMonad-Hooks-DynamicLog.html">
XMonad.Hooks.DynamicLog</a> puede verse una forma sencilla de adaptar <strong>statusbar</strong> para <strong>dzen2</strong>:
</p>

{% highlight haskell %}
---
--- dzen Dock
---
myDzen :: LayoutClass l Window
     => XConfig l -> IO (XConfig (ModifiedLayout AvoidStruts l))
myDzen conf = statusBar ("dzen2 " ++ flags) myPP toggleStrutsKey conf
 where
    fg      = "'#a8a3f7'"
    bg      = "'#000000'"
    flags   = "-dock -e 'onstart=lower' -fn 'profont-8' -x 0 -y 0 -w 500 -h 20 -ta l -fg " ++ fg ++ " -bg " ++ bg

toggleStrutsKey :: XConfig t -> (KeyMask, KeySym)
toggleStrutsKey XConfig{modMask = modm} = (modm .|. shiftMask, xK_Print )
{% endhighlight %}
<br />
<p style="text-align:justify"> El código fuente preliminar puede consultarse en
<a href="https://github.com/cattena/xmonad-configs">github</a>. 
</p>



