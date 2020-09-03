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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "74294570"
---
# <a name="display-data-in-blend"></a>Отображение данных в Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При настройке макета страниц вы можете просмотреть демонстрационные данные в конструкторе. Демонстрационные данные можно создать с нуля или с помощью существующего класса. Вы также можете подключиться к *динамическим данным* , которые появятся в вашем приложении при его запуске.

 **В этом разделе:**

- [Создание примера данных](#Scratch)

- [Создание демонстрационных данных из класса](#Existing)

- [Отображение динамических данных в приложении WPF](#LiveWPF)

- [Отображение динамических данных в приложении магазина или телефона](#LiveStore)

## <a name="generate-sample-data"></a><a name="Scratch"></a> Создание демонстрационных данных
 Чтобы создать демонстрационные данные, откройте XAML-документ. На панели **Данные** нажмите кнопку **Создать демонстрационные данные**![](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") и выберите **Новые демонстрационные данные**.

 Определить структуру данных можно на панели **Данные** , а затем привязать ее к элементам пользовательского интерфейса на любой странице.

 ![](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png "496d7ebc-fe46-42f6-95a8-57b0e5be5d49")

 Если требуется, чтобы демонстрационные данные отображались на страницах при запуске приложения, нажмите элемент **Параметры источника данных** ![](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png "ae1fd260-4f84-420d-b196-45fde357d81d"), а затем щелкните **Разрешить при выполнении приложения**.

 ![](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png "05d5356d-91bb-4e6b-b3f7-29b76852c4b3")

 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [создание демонстрационных данных с нуля](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [для объединения некоторых привязок данных с помощью Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="generate-sample-data-from-a-class"></a><a name="Existing"></a> Создание демонстрационных данных из класса
 Если вы уже создали классы, которые описывают структуру данных, вы можете создать демонстрационные данные на их основе.

 Чтобы создать демонстрационные данные на основе класса, откройте XAML-документ и на панели **Данные** нажмите кнопку **Создать демонстрационные данные**![](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") , а затем щелкните **Создать демонстрационные данные из класса**.

 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [создание демонстрационных данных из класса](https://channel9.msdn.com/Shows/Inside+Windows+Phone/IWP54--Windows-Phone-Data-Binding-and-the-Magic-of-XAML).

 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [для объединения некоторых привязок данных с помощью Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="show-live-data-in-a-wpf-application"></a><a name="LiveWPF"></a> Отображение динамических данных в приложении WPF
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Создание источника данных XML](https://www.youtube.com/watch?v=RjQueappjqk&feature=youtube_gdata).

## <a name="show-live-data-in-a-store-or-phone-app"></a><a name="LiveStore"></a> Отображение динамических данных в приложении магазина или телефона
 См. раздел [Работа с данными и файлами (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/br229562.aspx).

## <a name="see-also"></a>См. также:
 [Создание пользовательского интерфейса с помощью Blend для Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
