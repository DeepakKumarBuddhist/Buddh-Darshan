# Buddh-Darshan
इसमें बुद्ध की महिमा और उनके कृपा  का   विवरण मिलेगा 
import 'package:flutter/material.dart';

void main() { runApp(const BuddhaDarshanApp()); }

class BuddhaDarshanApp extends StatelessWidget { const BuddhaDarshanApp({super.key});

@override Widget build(BuildContext context) { return MaterialApp( title: 'Buddha Darshan - Deepak Kumar', theme: ThemeData( useMaterial3: true, colorSchemeSeed: Colors.teal, ), debugShowCheckedModeBanner: false, home: const HomeScreen(), ); } }

class HomeScreen extends StatelessWidget { const HomeScreen({super.key});

@override Widget build(BuildContext context) { return SafeArea( child: Scaffold( appBar: AppBar(title: const Text('Buddha Darshan - Deepak Kumar')), body: ListView( padding: const EdgeInsets.all(16), children: [ Card( shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)), child: const Padding( padding: EdgeInsets.all(16), child: Text( 'Welcome to Buddha Darshan – Deepak Kumar.\n\nयह ऐप बुद्ध के जीवन, विचारों और प्रेरक कहानियों को समर्पित है। इसमें आप हमारे काम के बारे में जान सकते हैं, वालेंटियर के रूप में जुड़ सकते हैं और दान भी कर सकते हैं।', style: TextStyle(fontSize: 15, height: 1.5), ), ), ), const SizedBox(height: 16), ListTile( leading: const Icon(Icons.info, color: Colors.teal), title: const Text('About Us'), onTap: () {}, ), ListTile( leading: const Icon(Icons.work, color: Colors.teal), title: const Text('Our Work'), onTap: () {}, ), ListTile( leading: const Icon(Icons.menu_book, color: Colors.teal), title: const Text('Stories of Buddha'), onTap: () { Navigator.push( context, MaterialPageRoute(builder: (context) => const StoriesScreen()), ); }, ), ListTile( leading: const Icon(Icons.group_add, color: Colors.teal), title: const Text('Volunteer Apply'), onTap: () { Navigator.push( context, MaterialPageRoute(builder: (context) => const VolunteerForm()), ); }, ), ListTile( leading: const Icon(Icons.favorite, color: Colors.teal), title: const Text('Donate'), onTap: () { Navigator.push( context, MaterialPageRoute(builder: (context) => const DonationForm()), ); }, ), ], ), ), ); } }

class StoriesScreen extends StatelessWidget { const StoriesScreen({super.key});

@override Widget build(BuildContext context) { final stories = <_StoryData>[ _StoryData( title: 'सिद्धार्थ का जन्म', detail: 'लुंबिनी उपवन में महारानी माया देवी ने एक राजकुमार को जन्म दिया। बाद में वही सिद्धार्थ गौतम बुद्ध बने।', ), _StoryData( title: 'दुख के दर्शन', detail: 'राजमहल से बाहर निकलते समय सिद्धार्थ ने वृद्ध, रोगी, मृतक और सन्यासी को देखा। यहीं से जीवन के दुःख और मुक्ति की खोज शुरू हुई।', ), _StoryData( title: 'ज्ञान प्राप्ति', detail: 'बोधगया में पीपल के वृक्ष के नीचे गहन ध्यान के बाद सिद्धार्थ ने ज्ञान प्राप्त किया और बुद्ध कहलाए।', ), _StoryData( title: 'प्रथम उपदेश', detail: 'वाराणसी के सारनाथ में बुद्ध ने पंचवर्गीय भिक्षुओं को “धम्मचक्कपवत्तन सूत्र” का उपदेश दिया।', ), _StoryData( title: 'महापरिनिर्वाण', detail: '८० वर्ष की आयु में कुशीनगर में बुद्ध ने महापरिनिर्वाण प्राप्त किया।', ), ];

return SafeArea(
  child: Scaffold(
    appBar: AppBar(title: const Text('बुद्ध की कहानियाँ - Buddha Darshan')), 
    body: ListView.separated(
      padding: const EdgeInsets.all(16),
      itemCount: stories.length + 1,
      separatorBuilder: (_, __) => const SizedBox(height: 12),
      itemBuilder: (context, i) {
        if (i == stories.length) {
          return Card(
            shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)),
            child: const Padding(
              padding: EdgeInsets.all(16),
              child: Text(
                'यह ऐप Deepak Kumar द्वारा तैयार किया गया है।',
                style: TextStyle(fontSize: 15, fontWeight: FontWeight.w500),
              ),
            ),
          );
        }
        final s = stories[i];
        return Card(
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)),
          child: Padding(
            padding: const EdgeInsets.all(16),
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                Text(s.title, style: const TextStyle(fontSize: 18, fontWeight: FontWeight.bold)),
                const SizedBox(height: 8),
                Text(s.detail, style: const TextStyle(fontSize: 15, height: 1.5)),
              ],
            ),
          ),
        );
      },
    ),
  ),
);

} }

class VolunteerForm extends StatelessWidget { const VolunteerForm({super.key});

@override Widget build(BuildContext context) { final nameController = TextEditingController(); final contactController = TextEditingController();

return Scaffold(
  appBar: AppBar(title: const Text('Volunteer Apply')), 
  body: Padding(
    padding: const EdgeInsets.all(16),
    child: Column(
      children: [
        TextField(
          controller: nameController,
          decoration: const InputDecoration(labelText: 'Name'),
        ),
        TextField(
          controller: contactController,
          decoration: const InputDecoration(labelText: 'Contact Info'),
        ),
        const SizedBox(height: 20),
        ElevatedButton(
          onPressed: () {
            ScaffoldMessenger.of(context).showSnackBar(
              SnackBar(content: Text('Application submitted: ${nameController.text}')),
            );
          },
          child: const Text('Submit'),
        )
      ],
    ),
  ),
);

} }

class DonationForm extends StatelessWidget { const DonationForm({super.key});

@override Widget build(BuildContext context) { final nameController = TextEditingController(); final amountController = TextEditingController();

return Scaffold(
  appBar: AppBar(title: const Text('Donate')), 
  body: Padding(
    padding: const EdgeInsets.all(16),
    child: Column(
      children: [
        TextField(
          controller: nameController,
          decoration: const InputDecoration(labelText: 'Name'),
        ),
        TextField(
          controller: amountController,
          decoration: const InputDecoration(labelText: 'Amount'),
          keyboardType: TextInputType.number,
        ),
        const SizedBox(height: 20),
        ElevatedButton(
          onPressed: () {
            ScaffoldMessenger.of(context).showSnackBar(
              SnackBar(content: Text('Donation submitted: ${amountController.text}')),
            );
          },
          child: const Text('Submit'),
        )
      ],
    ),
  ),
);

} }

class _StoryData { final String title; final String detail; const _StoryData({required this.title, required this.detail}); }

