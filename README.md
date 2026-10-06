# 360 Person Remover

Merge two equirectangular (360°) photos into one and remove the photographer from the shot.

Take one photo standing behind the camera and a second standing in front of it. Mark where the person appears in the first photo, and the app fills that area from the second.

Everything runs in your browser. Photos are never uploaded anywhere.


## Screenshots
**1. Mark the people in Photo A.** Painted areas (red) will be replaced with the matching area from Photo B.

<img width="2560" height="1080" alt="360-person-remover" src="https://github.com/user-attachments/assets/65b1a620-f8bc-4839-a1b8-874968f30d41" />


**2. Check the result.** The people are gone and the grass and paths are filled in from Photo B.

<img width="2560" height="1080" alt="360-person-remover_result" src="https://github.com/user-attachments/assets/d6bc9e92-c2a9-4395-8ad2-03a997a57725" />


## Quick start

1. Download the app. Either:
   - Select the green **Code** button, then **Download ZIP**, and unzip it; or
   - Open `360-person-remover.html` in this repository, select the **Download raw file** button (the download icon above the file), and save it.
2. Double-click `360-person-remover.html` to open it in Chrome, Edge, Firefox or Safari.

No install, server or Git knowledge is needed.

## Taking the photos

- Put the camera on a tripod and don't move it between shots.
- Photo A: stand directly behind the camera.
- Photo B: stand directly in front of the camera, on the opposite side.
- Keep the camera height, exposure and white balance the same for both. Lock exposure if your camera allows it.
- Make sure the area where the person stands in A is clear of the person in B. Opposite sides of the camera work best.

## Using the app

1. **Load photos.** Choose Photo A (person behind) and Photo B (person in front).
2. **Align B to A.** Only needed if the camera moved slightly. Use the yaw and tilt sliders and check the *Photo B* and *Result* tabs.
3. **Mark the person in Photo A.** Paint over them, slightly wider than their outline. Painted areas are replaced with Photo B.
   - *Paint / Erase* edits the mask. *Undo* (Ctrl/Cmd+Z) and *Clear* are also available.
   - *Edge softness* feathers the join so the seam is less visible.
   - *Wedge* marks a whole direction at once. Centre is in degrees, where 0° is the middle of the image and ±180° is the left/right seam. For example, a person directly behind the camera is about 180°, width 60°.
4. **Check the Result tab**, then choose JPEG or PNG and select **Save merged image**.

The preview is limited to 2048 px wide so painting stays responsive. The saved file uses the full resolution of Photo A.

## Tips

- Both images should be in the same equirectangular layout and ideally the same size. If they differ, Photo B is stretched to match Photo A.
- Painting wraps around the left and right edges, so a person standing at the seam is handled correctly.
- Use the zoom control (2× or 4×) for precise painting around edges.
- Pick PNG if you plan to edit the result further.

## Known limitations

- The person is marked manually; there is no automatic detection.
- No exposure matching. If the light changed between shots, you may see a faint seam. Increase edge softness to hide it.
- Saving removes 360 metadata (XMP). Some viewers (Facebook, Google Photos) may show the image flat. Re-tag it with [exiftool](https://exiftool.org) or your camera's app, for example:

  ```bash
  exiftool -XMP-GPano:ProjectionType=equirectangular \
           -XMP-GPano:UsePanoramaViewer=True merged-360.jpg
  ```

- Very large images (over about 16 MP) may fail to save on iPhones and iPads because of browser canvas limits.

## Created with Claude

This tool was designed and written by [Claude](https://claude.ai), an AI assistant made by [Anthropic](https://www.anthropic.com), through a conversation with the repository owner. The owner directed the project and tested the result.

## Status

This project is shared as-is. It is not actively maintained and contributions (issues, pull requests) are not being accepted. You are free to copy the single `index.html` file and adapt it for your own use. It has no build step or dependencies.

Work on copies of your photos rather than your originals.


## License

Choose a license when you create the repository (MIT is a common choice for small tools) and add a `LICENSE` file.
