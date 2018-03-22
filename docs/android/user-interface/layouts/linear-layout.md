---
title: LinearLayout
ms.topic: article
ms.prod: xamarin
ms.assetid: B49D129C-AF24-3C5A-C833-5A34AFBB2442
ms.technology: xamarin-android
author: mgmclemore
ms.author: mamcle
ms.date: 02/06/2018
ms.openlocfilehash: fc6bc9e1d4625f8f45887b0a144a31383046b296
ms.sourcegitcommit: 30055c534d9caf5dffcfdeafd6f08e666fb870a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2018
---
# <a name="linearlayout"></a>LinearLayout

[`LinearLayout`](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/) ist eine [ `ViewGroup` ](https://developer.xamarin.com/api/type/Android.Views.ViewGroup/) , anzeigt, dass untergeordnete [ `View` ](https://developer.xamarin.com/api/type/Android.Views.View/) Elemente in einer linearen Richtung entweder vertikal oder horizontal.

Sie sollte mit Vorsicht zu stark verwendet die [ `LinearLayout` ](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/).
Wenn Sie bereits begonnen haben Schachteln mehrerer [ `LinearLayout` ](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/)s, Sie sollten erwägen, eine [ `RelativeLayout` ](https://developer.xamarin.com/api/type/Android.Widget.RelativeLayout/) stattdessen.

Starten Sie ein neues Projekt mit dem Namen **HelloLinearLayout**.

Open **Resources/Layout/Main.axml** , und fügen Sie Folgendes:

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation=    "vertical"
    android:layout_width=    "fill_parent"
    android:layout_height=    "fill_parent"    >

  <LinearLayout
      android:orientation=    "horizontal"
      android:layout_width=    "fill_parent"
      android:layout_height=    "fill_parent"
      android:layout_weight=    "1"    >
      <TextView
          android:text=    "red"
          android:gravity=    "center_horizontal"
          android:background=    "#aa0000"
          android:layout_width=    "wrap_content"
          android:layout_height=    "fill_parent"
          android:layout_weight=    "1"    />
      <TextView
          android:text=    "green"
          android:gravity=    "center_horizontal"
          android:background=    "#00aa00"
          android:layout_width=    "wrap_content"
          android:layout_height=    "fill_parent"
          android:layout_weight=    "1"    />
      <TextView
          android:text=    "blue"
          android:gravity=    "center_horizontal"
          android:background=    "#0000aa"
          android:layout_width=    "wrap_content"
          android:layout_height=    "fill_parent"
          android:layout_weight=    "1"    />
      <TextView
          android:text=    "yellow"
          android:gravity=    "center_horizontal"
          android:background=    "#aaaa00"
          android:layout_width=    "wrap_content"
          android:layout_height=    "fill_parent"
          android:layout_weight=    "1"    />
  </LinearLayout>
        
  <LinearLayout
    android:orientation=    "vertical"
    android:layout_width=    "fill_parent"
    android:layout_height=    "fill_parent"
    android:layout_weight=    "1"    >
    <TextView
        android:text=    "row one"
        android:textSize=    "15pt"
        android:layout_width=    "fill_parent"
        android:layout_height=    "wrap_content"
        android:layout_weight=    "1"    />
    <TextView
        android:text=    "row two"
        android:textSize=    "15pt"
        android:layout_width=    "fill_parent"
        android:layout_height=    "wrap_content"
        android:layout_weight=    "1"    />
    <TextView
        android:text=    "row three"
        android:textSize=    "15pt"
        android:layout_width=    "fill_parent"
        android:layout_height=    "wrap_content"
        android:layout_weight=    "1"    />
    <TextView
        android:text=    "row four"
        android:textSize=    "15pt"
        android:layout_width=    "fill_parent"
        android:layout_height=    "wrap_content"
       android:layout_weight=    "1"    />
  </LinearLayout>

</LinearLayout>
```

Prüfen Sie sorgfältig, diese XML-Daten. Es ist ein Stamm [ `LinearLayout` ](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/) , definiert die Ausrichtung auf vertikal &ndash; alle untergeordneten [ `View` ](https://developer.xamarin.com/api/type/Android.Views.View/)s (von dem die It zwei hat) werden vertikal gestapelt werden. Das erste untergeordnete Element ist ein weiterer [ `LinearLayout` ](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/) , verwendet eine horizontale Ausrichtung und das zweite untergeordnete Element ist ein [ `LinearLayout` ](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/) , verwendet eine vertikale Ausrichtung. Jede dieser geschachtelten [ `LinearLayout` ](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/)s enthalten mehrere [ `TextView` ](https://developer.xamarin.com/api/type/Android.Widget.TextView/) Elemente, die miteinander in der Weise, die durch das übergeordnete Objekt definierten ausgerichtet sind [ `LinearLayout` ](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/).

Jetzt öffnen **HelloLinearLayout.cs** und stellen Sie sicher, lädt er die **Resources/Layout/Main.axml** Layout in der [ `OnCreate()` ](https://developer.xamarin.com/api/member/Android.App.Activity.OnCreate/p/Android.OS.Bundle/) Methode:

```csharp
protected override void OnCreate (Bundle savedInstanceState)
{
    base.OnCreate (savedInstanceState);
    SetContentView (Resource.Layout.Main);
}
```

Die [ `SetContentView(int)` ](https://developer.xamarin.com/api/member/Android.App.Activity.SetContentView/(System.Int32)) Methode lädt die Layoutdatei für die [ `Activity` ](https://developer.xamarin.com/api/type/Android.App.Activity/), durch die Ressourcen-ID angegebene &ndash; `Resources.Layout.Main` bezieht sich auf die **Ressourcen/Layout / Main.axml** Layoutdatei.

Führen Sie die Anwendung aus. Sie sollten Folgendes angezeigt:

[![Screenshot der app, die erste LinearLayout horizontal angeordnet, die zweite vertikal](linear-layout-images/helloviews1.png)](linear-layout-images/helloviews1.png#lightbox)

Beachten Sie, wie die XML-Attribute für jede Ansicht Verhalten definieren. Probieren Sie verschiedene Werte für `android:layout_weight` basierend auf die Gewichtung der einzelnen Elemente finden Sie unter wie die Bildschirmfläche verteilt wird. Finden Sie unter der [allgemeine Layoutobjekte](http://developer.android.com/guide/topics/ui/declaring-layout.html) Dokument Weitere Informationen dazu, wie [ `LinearLayout` ](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/) behandelt die `android:layout_weight` Attribut.


## <a name="references"></a>Verweise

-   [`LinearLayout`](https://developer.xamarin.com/api/type/Android.Widget.LinearLayout/) 
-   [`TextView`](https://developer.xamarin.com/api/type/Android.Widget.TextView/) 

*Teile dieser Seite werden basierend auf der Arbeit erstellt und von Android Open Source-Projekt gemeinsam genutzt und verwendet entsprechend Begriffe, die in beschriebenen Änderungen der*
[*Creative Commons 2.5 Namensnennung Lizenz* ](http://creativecommons.org/licenses/by/2.5/).
