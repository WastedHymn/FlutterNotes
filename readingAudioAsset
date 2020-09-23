//LOADING AUDIO FILE FROM ASSETS FOLDER
void loadSoundAsset() async {
    final ByteData data = await rootBundle.load('assets/mp3/Doomsday.mp3');
    Directory tempDir = await getTemporaryDirectory();
    File tempFile = File('${tempDir.path}/Doomsday.mp3');
    await tempFile.writeAsBytes(data.buffer.asUint8List(), flush: true);
    print(tempFile.path.toString());
    final Map map = await tagger.readTagsAsMap(path: tempFile.path);
    print("MAP!\n${map}");
  }
  
  //LOADING AUDIO FILE FROM DEVICE STORAGE
  void getTagsAsMap() async {
    final dir = await getApplicationDocumentsDirectory();
    final file = new File("${dir.path}/Doomsday.mp3");
    print("Exist: ${await file.exists()}");
    if(!(await file.exists())){
      final soundData = await rootBundle.load(file.path);
      final bytes = soundData.buffer.asUint8List();
      await file.writeAsBytes(bytes, flush: true);
    }
    final Map map = await tagger.readTagsAsMap(path: file.path);
    print("MAP");
    map.forEach((key, value) {
      print("KEY: ${key} VALUE:${value}");
    });
