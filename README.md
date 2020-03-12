# MeetupRSK-Xablu

# Blockchain for developer
This repository show how to start coding in RSK in mobile apps

Speakers
Dulce Villarreal
Dulce  is a Developer Advocate with RSK on the San Francisco City Team focusing on Blockhain and Fintech. With a background in economie  she works with startups and developers to help them adopt Blockchain and Fintech, talks at industry events and spends her weekends at hackathons.

Sebastian Perez
Mobile & Blockchain Developer. Microsoft MVP. Enthusiast of disruptive technologies, looking for innovational projects that generate a positive impact on society. Software developer since more than 10 years, with experience in Web, Mobile and Blockchain. Sportsman, basketball fan.

# Agenda:
6:00 pm Latinx food and networking
6:30 pm Discussion: Mobile Apps Security
7:00 pm Worshop: using Nethereum to connect to a RSK-node
7:30 pm Q&A
8:30 Wrap up

# Outline

# Requirements:

Workshop:
- [Visual Studio Community 2019 installed with Xamarin](https://visualstudio.microsoft.com/vs/community/)
-  Add Android SDK & emulator



# Important URLS:
https://visualstudio.microsoft.com/vs/community/
http://rsk.co

## Prerequisites
Basic development knowledge.

## Workshop
1. Open Visual Studio, and Create a new Blank Form Apps (Cross Platform)
2. Check that Xamarin.Essentials is installed. If not, then install it from NuGet.
3. Edit Main Page StackLayout Tag:
```
  <StackLayout>
    <Entry Placeholder="Address" x:Name="entryAddress" />
    <Entry Placeholder="Key" x:Name="entryKey" />
    <Button Text="Store" Clicked="StoreKey"/>
  </StackLayout>
```
4. Edit Main.xaml.cs, adding:
```
  async void StoreKey(System.Object sender, System.EventArgs e)
  {
      try
      {
          await SecureStorage.SetAsync("user-address", entryAddress.Text);
          await SecureStorage.SetAsync("user-key", entryKey.Text);
      }
      catch (Exception exc)
      {
          await DisplayAlert("Error","There was a problem storing user information","OK");
      }
  }
```
5. Create a new ContentPage, then edit construtor:
```
InitializeComponent();
var userAddress = await SecureStorage.GetAsync("user-address");
var userKey = await SecureStorage.GetAsync("user-key");
```
6. Install Nethereum from NuGet
7. Get your account balance:
```
var web3 = new Web3("https://public-node.testnet.rsk.co");
var balance = await web3.Eth.GetBalance.SendRequestAsync(userAddress);
```
8. Send transaction:
```
var account = new Account(userKey);
var transaction = await web3.Eth.GetEtherTransferService()
            .TransferEtherAndWaitForReceiptAsync(otherAddress, 1m);
```



