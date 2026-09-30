# AR Furniture Viewer

**Explore furniture models through a Unity AR prototype.**

A scene-based project with a furniture selector, touch rotation, pinch scaling, and Vuforia camera integration.

`Unity 2022.3.45f1` · `C#` · `Vuforia` · `Android / AR`

[Open the project](#open-the-project) · [Interactions](#interactions) · [Code map](#code-map)

This repository is a fork of [Kaytbay/AR-Testing-](https://github.com/Kaytbay/AR-Testing-). The upstream project, contributors, and individual asset authors retain their attribution.

---

## The experience

The build configuration lists two scenes:

| Scene | Role |
| :--- | :--- |
| [MainMenu](Assets/Scenes/MainMenu.unity) | Entry screen |
| [SampleScene](Assets/Scenes/SampleScene.unity) | AR experience loaded by the menu |

Furniture objects can be selected from a configured collection. Interaction scripts rotate and scale the active models, and the camera script requests continuous autofocus after Vuforia starts.

## Open the project

1. Clone this repository and add its root folder through Unity Hub.
2. Use **Unity 2022.3.45f1**, matching [ProjectVersion.txt](ProjectSettings/ProjectVersion.txt).
3. Restore the Vuforia dependency described below before expecting a successful import.
4. Open `Assets/Scenes/MainMenu.unity`.
5. Inspect the camera, image-target, furniture-array, and UI references in the scenes.
6. For device testing, install the appropriate Unity platform build support and configure the target device and Vuforia settings.

### Dependency to restore

[Packages/manifest.json](Packages/manifest.json) references the local archive:

```text
Packages/com.ptc.vuforia.engine-11.1.3.tgz
```

That archive is **not included in the repository**. Obtain the matching package through the official Vuforia distribution, or update the dependency intentionally for your environment. The manifest also lists ARCore 5.1.6 and XR Management 4.5.1; those entries alone do not establish device compatibility.

This is a prototype source repository, not a verified one-click mobile build.

## Interactions

| Environment | Input | Behavior |
| :--- | :--- | :--- |
| Touch device | One-finger drag | Rotate the model |
| Touch device | Two-finger pinch | Scale the model within configured bounds |
| Unity Editor | Click and drag over the model collider | Test rotation |
| Unity Editor | Mouse wheel | Test scaling |
| UI | Furniture selection | Activate the chosen model |

Editor interaction tests do not replace testing camera tracking on a supported device.

## Code map

| Script | Responsibility |
| :--- | :--- |
| [ChangeFurnitures.cs](Assets/Scripts/ChangeFurnitures.cs) | Switch between configured furniture objects |
| [RotateAndPinch.cs](Assets/Scripts/RotateAndPinch.cs) | Touch and editor interactions |
| [CameraFocus.cs](Assets/Scripts/CameraFocus.cs) | Vuforia autofocus request |
| [MenuController.cs](Assets/Scripts/MenuController.cs) | Transition into the AR scene |

## Assets & attribution

The repository includes furniture models, materials, textures, audio, and third-party Unity content. Several model folders contain their own `license.txt` files; retain those files and check the corresponding asset terms before redistribution.

[Assets](Assets) · [Package manifest](Packages/manifest.json) · [Build scenes](ProjectSettings/EditorBuildSettings.asset)
