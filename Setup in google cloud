// get list of all files from a Particular bucket
router.get("/getAllFilesFromParticularBucket", Auth.userAuthMiddleWare, async (req, res) => {
    try {
        const bucketName = req.body.bucketName;
        const directoryPath = path.join(`bucketFolder/${bucketName}`);
        fs.readdir(directoryPath, (err, files) => {
            if (err) {
                return res.json({ status: false, message: `${bucketName}, No Such Bucket Found` });
            }

            const allfiles = files.filter(file => {
                const filePath = path.join(directoryPath, file);
                return fs.statSync(filePath).isFile();
            });

            console.log(allfiles);
            return res.json({ status: true, filesList: allfiles });
        });
    } catch (error) {
        console.log("error------->>", error);
    }
});
