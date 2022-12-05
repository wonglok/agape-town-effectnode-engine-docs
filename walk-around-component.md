---
description: Just like a done's view of an avatar
---

# 🚶♀ Walk around Component

```jsx
  ...
  
  let gltf = useGLTF('/scene/myplace.glb');
  
  let floor = useMemo(() => {
    let floor = SkeletonUtils.clone(gltf.scene);
    return floor;
  }, [gltf]);

  let colliderManager = useMemo(() => {
    return new ColliderManager({ floor, scene: get().scene });
  }, [floor]);
  
  return <group>
  
      <PlayerDisplay Now={Now} floor={floor}>
        <PlayerCollider
          Now={Now}
          colliderMesh={colliderManager.collider}
        ></PlayerCollider>
      </PlayerDisplay>

      <SkyViewControls
        colliderMesh={colliderManager.collider}
        Now={Now}
      ></SkyViewControls>
      
      <primitive object={floor}></pimitive>
  </group>
  
  

  
```

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption><p><a href="https://metaverse.effectnode.com/place/church">https://metaverse.effectnode.com/place/church</a></p></figcaption></figure>

