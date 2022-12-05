---
description: Visual Effect / Physics Simulation
---

# ✨ Physics Particle Simulation with Lines Realtime Rendering

```jsx

function FunSimCom() {
  // let { get } = useThree();
  let { mini, get } = useMiniEngine();

  let cursorPointer = useMemo(() => {
    return new Vector3();
  }, []);

  let sim = useMemo(() => {
    return new FunSim({
      cursorPointer: cursorPointer,
      node: mini,
      influences: [
        {
          type: `computeSphere`,
          enabled: true,
          mouse: true,
          needsUpdate: true,
          position: { x: 0, y: 0, z: 0 },
          radius: 2,
          force: 35.0,
          noise: 3.0,
        },

        {
          type: `computeSphere`,
          enabled: true,
          mouse: false,
          needsUpdate: true,
          position: { x: 0, y: 0, z: 0 },
          radius: 1.5,
          force: -30.0,
          noise: 3.0,
        },

        //
        // {
        //   type: `computeGravity`,
        //   enabled: true,
        //   direction: { x: 0, y: -1, z: 0 },
        //   force: -1,
        // },
      ],
      tailLength: 64, // 512, 1024
      howManyTrackers: 2048,
    });
  }, [mini, cursorPointer]);

  useFrame(() => {
    sim.track();
  });

  useEffect(() => {
    window.addEventListener("gridPt", ({ detail }) => {
      sim.influences
        .filter((e) => {
          return e.mouse;
        })
        .forEach((e) => {
          e.position.x = detail.x;
          e.position.y = detail.y;
          e.position.z = detail.z;
          e.needsUpdate = true;
        });
    });
  });

  return (
    <group position={[0, 0, 0]}>
      {/* <DOrbit /> */}
      <Visualise influ={sim.influences} />
      <primitive object={sim.o3d}></primitive>
    </group>
  );
}
```

{% embed url="https://github.com/wonglok/effectnode-metaverse/blob/master/vfx/places/simulation/SimPage.js" %}
Open Source Code
{% endembed %}

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption><p><a href="https://metaverse.effectnode.com/place/simulation">https://metaverse.effectnode.com/place/simulation</a></p></figcaption></figure>

