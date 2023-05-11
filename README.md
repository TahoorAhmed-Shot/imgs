# imgs

  function handleFileChange(event) {
    const files = event.target.files;
    const newImageSrcs = [...imageSrcs];

    for (let i = 0; i < files.length; i++) {
      const file = files[i];
      const reader = new FileReader();
      reader.readAsDataURL(file);
      console.log(file);
      reader.addEventListener("load", function () {
        const base64 = reader.result.split(",").pop();
        newImageSrcs.push({
          image: base64,
          localImage: reader.result,
          imagePath: file.name,
          extension: JSON.parse(JSON.stringify(file.name.split(".").pop())),
        });
        setImageSrcs(newImageSrcs);
      });
    }
  }
