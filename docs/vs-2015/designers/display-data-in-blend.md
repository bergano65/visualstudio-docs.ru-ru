---
title: Отображение данных в Blend | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2ed51eaef8594695d4d594401ab9375563525b10
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294570"
---
# <a name="display-data-in-blend"></a>Отображение данных в Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При настройке макета страниц вы можете просмотреть демонстрационные данные в конструкторе. Демонстрационные данные можно создать с нуля или с помощью существующего класса. Вы также можете подключиться к *динамическим данным* , которые появятся в вашем приложении при его запуске.

 **Содержание раздела**

- [Создание демонстрационных данных](#Scratch)

- [Создание демонстрационных данных из класса](#Existing)

- [Отображение динамических данных в приложении WPF](#LiveWPF)

- [Отображение динамических данных в приложении Магазина или в приложении для телефона](#LiveStore)

## <a name="Scratch"></a> Создание демонстрационных данных
 Чтобы создать демонстрационные данные, откройте XAML-документ. In the **Data** panel, choose the **Create sample data**![](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") button, and then choose **New Sample Data**.

 Определить структуру данных можно на панели **Данные** , а затем привязать ее к элементам пользовательского интерфейса на любой странице.

 ![](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png "496d7ebc-fe46-42f6-95a8-57b0e5be5d49")

 If you want your sample data to appear in your pages when you run the app, choose **Data source options** ![](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png "ae1fd260-4f84-420d-b196-45fde357d81d"), and then choose **Enable When Running Application**.

 ![](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png "05d5356d-91bb-4e6b-b3f7-29b76852c4b3")

 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create sample data from scratch](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Mixing up some data binding with Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="Existing"></a> Создание демонстрационных данных из класса
 Если вы уже создали классы, которые описывают структуру данных, вы можете создать демонстрационные данные на их основе.

 To generate sample data from a class, open a XAML document, and then in the **Data** panel, click the **Create sample data**![](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") button, and then click **Create Sample Data from Class**.

 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create sample data from a class](https://channel9.msdn.com/Shows/Inside+Windows+Phone/IWP54--Windows-Phone-Data-Binding-and-the-Magic-of-XAML).

 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Mixing up some data binding with Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="LiveWPF"></a> Отображение динамических данных в приложении WPF
 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create an XML data source](https://www.youtube.com/watch?v=RjQueappjqk&feature=youtube_gdata).

## <a name="LiveStore"></a> Отображение динамических данных в приложении Магазина или в приложении для телефона
 См. раздел [Работа с данными и файлами (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/br229562.aspx).

## <a name="see-also"></a>См. также раздел
 [Создание пользовательского интерфейса с помощью Blend для Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
