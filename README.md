# mydropdownmenue
return Card(
       elevation: 54,
       child: Scaffold(
         appBar: AppBar(
           backgroundColor: Color(0xFF9A2E00),
           centerTitle: true,
           title: GestureDetector(
               child: Image.asset("assets/nbp.png",
                   height: 50, width: 100, color: Colors.white),
               onTap: () {
                 Navigator.push(
                     context, MaterialPageRoute(builder: (context) => home()));
               }),
           actions: [
             Card(
               elevation: 5,
               child: Theme(
                 data: Theme.of(context).copyWith(
                     textTheme: TextTheme().apply(bodyColor: Colors.green),
                     dividerColor: Colors.white,
                     iconTheme: IconThemeData(color: Colors.white)),
                 child: PopupMenuButton<int>(
                   color: Color(0xFFFB9B4E),
                   itemBuilder: (context) => [
                     PopupMenuItem<int>(
                         value: 0,
                         child: Row(
                           children: [
                             Icon(Icons.settings),
                             const SizedBox(
                               width: 7,
                             ),
                             Text("Setting"),
                           ],
                         )),
                     PopupMenuItem<int>(
                         value: 1,
                         child: Row(
                           children: [
                             Icon(Icons.policy),
                             const SizedBox(
                               width: 7,
                             ),
                             Text("Privacy Policy page"),
                           ],
                         )),
                     PopupMenuDivider(),
                     PopupMenuItem<int>(
                         value: 2,
                         child: Row(
                           children: [
                             Icon(
                               Icons.logout,
                               color: Colors.white,
                             ),
                             const SizedBox(
                               width: 7,
                             ),
                             Text("Logout")
                           ],
                         )),
                   ],
                   onSelected: (item) => SelectedItem(context, item),
                 ),
               ),
             ),
           ],
         ),
         body: Container(),
       ),
     );
   }
 
   void SelectedItem(BuildContext context, item) {
     switch (item) {
       case 0:
         Navigator.of(context)
             .push(MaterialPageRoute(builder: (context) => home()));
         break;
       case 1:
         print("Privacy Clicked");
         break;
       case 2:
         print("User Logged out");
         Navigator.of(context).pushAndRemoveUntil(
             MaterialPageRoute(builder: (context) => home()), (route) => false);
         break;
     }
   }
 }
