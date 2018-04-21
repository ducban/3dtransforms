---

title: Perspective
layout: doc
category: docs
script: perspective.js

---


To activate 3D space, an element needs perspective.  This can be applied in two ways: using the `transform` property, with the perspective as a functional notation:


{% highlight css %}
transform: perspective(600px);
{% endhighlight %}

For example:

{% highlight css %}
.panel--red {
  /* perspective function in transform property */
  transform: perspective(600px) rotateY(45deg);
}
{% endhighlight %}

<div class="example example--set-persp">
  <div class="set-persp-panel set-persp-panel--red"></div>
</div>

Or you can use the `perspective` property:

{% highlight css %}
perspective: 600px;
{% endhighlight %}

For example:

{% highlight css %}
.example--blue {
  /* perspective property */
  perspective: 600px;
}

.panel--blue {
  transform: rotateY(45deg);
}
{% endhighlight %}

<div class="example example--set-persp example--set-persp--blue">
  <div class="set-persp-panel set-persp-panel--blue"></div>
</div>

These two formats both trigger a 3D space and produce the same visual result. But there is a difference. The functional notation is convenient for directly applying a 3D transform on a single element (in the red example, I use it in conjunction with a `rotateY` transform). But when used on multiple elements, the transformed elements don't line up together. If you use the same transform across elements with different positions, each element will have its own vanishing point. To remedy this, use the `perspective` property on a parent element, so each child may share the same 3D space.

{% highlight css %}
.panel--separate {
  transform: perspective(400px) rotateY(45deg);
}
{% endhighlight %}

<div class="example example--persp-children">
  <div class="persp-children-panel persp-children-panel--separate"></div>
  <div class="persp-children-panel persp-children-panel--separate"></div>
  <div class="persp-children-panel persp-children-panel--separate"></div>
  <div class="persp-children-panel persp-children-panel--separate"></div>
  <div class="persp-children-panel persp-children-panel--separate"></div>
  <div class="persp-children-panel persp-children-panel--separate"></div>
  <div class="persp-children-panel persp-children-panel--separate"></div>
  <div class="persp-children-panel persp-children-panel--separate"></div>
  <div class="persp-children-panel persp-children-panel--separate"></div>
</div>

{% highlight css %}
.example--together {
  perspective: 400px;
}

.panel--together {
  transform: rotateY(45deg);
}
{% endhighlight %}

<div class="example example--persp-children example--persp-children--together">
  <div class="persp-children-panel persp-children-panel--together"></div>
  <div class="persp-children-panel persp-children-panel--together"></div>
  <div class="persp-children-panel persp-children-panel--together"></div>
  <div class="persp-children-panel persp-children-panel--together"></div>
  <div class="persp-children-panel persp-children-panel--together"></div>
  <div class="persp-children-panel persp-children-panel--together"></div>
  <div class="persp-children-panel persp-children-panel--together"></div>
  <div class="persp-children-panel persp-children-panel--together"></div>
  <div class="persp-children-panel persp-children-panel--together"></div>
</div>

The value of `perspective` determines the intensity of the 3D effect. Think of it as a distance from the viewer to the object. The greater the value, the further the distance, the less intense the visual effect. `perspective: 2000px;` yields a subtle 3D effect, as if we are viewing an object from far away through binoculars. `perspective: 100px;` produces a tremendous 3D effect, like a tiny insect viewing a massive object.

By default, the vanishing point for a 3D space is positioned at the center. You can change the position of the vanishing point with `perspective-origin` property.

{% highlight css %}

perspective-origin: 25% 75%;

{% endhighlight %}

<div class="demo demo--persp-cube">
  <div class="example example--persp-cube">
    <div class="cube is-spinning is-backface-visible">
      <div class="cube__face cube__face--front">1</div>
      <div class="cube__face cube__face--back">2</div>
      <div class="cube__face cube__face--right">3</div>
      <div class="cube__face cube__face--left">4</div>
      <div class="cube__face cube__face--top">5</div>
      <div class="cube__face cube__face--bottom">6</div>
    </div>
  </div>
  <div class="options">
    <div class="options__row">
      <label>
        perspective
        <input class="perspective-range" type="range" min="1" max="2000" value="400" data-units="px" />
      </label>
    </div>
    <div class="options__row">
      <label>
        perspective-origin x
        <input class="origin-x-range" type="range" min="0" max="100" value="50" data-units="%" />
      </label>
    </div>
    <div class="options__row">
      <label>
        perspective-origin y
        <input class="origin-y-range" type="range" min="0" max="100" value="50" data-units="%" />
      </label>
    </div>
    <div class="options__row">
      <label>
        Spin cube
        <input class="spin-cube-checkbox" type="checkbox" />
      </label>
    </div>
    <div class="options__row">
      <label>
        Backface visible
        <input class="backface-checkbox" type="checkbox" checked />
      </label>
    </div>
  </div>
</div>

* * *

[**Next: 3D transform functions &raquo;**](3d-transform-functions.html)