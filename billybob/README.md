# Billybob illustrations

Upload the twelve story images directly into this folder, beside `index.html`:

```text
billybob/
  index.html
  BB_1.png
  BB_2.png
  BB_3.png
  BB_4.png
  BB_5.png
  BB_6.png
  BB_7.png
  BB_8.png
  BB_9.png
  BB_10.png
  BB_11.png
  BB_12.png
```

In GitHub, open `billybob/`, select **Add file → Upload files**, drag in the twelve PNG files, and commit the upload. Upload the images themselves, not the ZIP or a nested folder. Filenames are case-sensitive.

The reader already looks for these filenames in numerical order. No HTML changes are needed.

After all twelve images are added and checked, copy this folder to your S3 bucket under `billybob/`. The story is served at `/billybob/index.html`, or `/billybob/` when directory-index routing is configured.
