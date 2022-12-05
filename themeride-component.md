---
description: How to make theme ride
---

# 🎢 ThemeRide Component



<pre class="language-jsx"><code class="lang-jsx">...
  let gltf = useGLTF(`/scene/myplace.glb`);

    let floor = useMemo(() => {
    let floor = SkeletonUtils.clone(gltf.scene);
    return floor;
  }, [gltf]);

...
<strong>  &#x3C;WalkerFollowerControls floor={floor}>&#x3C;/WalkerFollowerControls>
</strong>....
</code></pre>

<figure><img src=".gitbook/assets/image (21).png" alt=""><figcaption><p><a href="https://metaverse.effectnode.com/place/spaceship">https://metaverse.effectnode.com/place/spaceship</a></p></figcaption></figure>
