# fab_menu

A FloatingActionButton with expandable menus

## Getting Started

```
class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => new _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  List<MenuData> menuDataList;

  @override
  void initState() {
    super.initState();
    menuDataList = [
      new MenuData(Icons.home, (context, menuData) {
        Scaffold.of(context).showSnackBar(
            new SnackBar(content: new Text('you have pressed ${menuData.labelText}')));
      },labelText: 'home'),
      new MenuData(Icons.sync_disabled, (context, menuData) {
        setState(() {
          menuData.enable = !menuData.enable;
          menuData.icon = menuData.enable? Icons.sync:Icons.sync_disabled;
        });
      },labelText: 'enable')
    ];
  }

  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: new AppBar(
        title: new Text(widget.title),
      ),
      body: new Center(
          child: new Text(
              'Remember to set floatingActionButtonLocation to fabMenuLocation')),
      floatingActionButton: new FabMenu(
        menus: menuDataList,
        maskColor: Colors.black,
      ),
      floatingActionButtonLocation: fabMenuLocation,
    );
  }
}
```
