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
ms.openlocfilehash: fa084ee92d7e262cb04661b4bbf26eefb74b9e06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664664"
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
 Чтобы создать демонстрационные данные, откройте XAML-документ. На панели **данные** нажмите кнопку **создать образец данных** ![ ](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") , а затем выберите **Новый образец данных**.

 Определить структуру данных можно на панели **Данные** , а затем привязать ее к элементам пользовательского интерфейса на любой странице.

 ![](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png "496d7ebc-fe46-42f6-95a8-57b0e5be5d49")

 Если вы хотите, чтобы образцы данных отображались на страницах при запуске приложения, выберите ![ ](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png "ae1fd260-4f84-420d-b196-45fde357d81d") **Параметры источника данных** , а затем выберите **включить при запуске приложения**.

 ![](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png "05d5356d-91bb-4e6b-b3f7-29b76852c4b3")

 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [создание демонстрационных данных с нуля](http://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [для объединения некоторых привязок данных с помощью Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="Existing"></a> Создание демонстрационных данных из класса
 Если вы уже создали классы, которые описывают структуру данных, вы можете создать демонстрационные данные на их основе.

 Чтобы создать демонстрационные данные из класса, откройте документ XAML, а затем на панели **данные** нажмите кнопку **создать образец** ![ ](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") данных, а затем выберите команду **создать демонстрационные данные из класса**.

 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [создание демонстрационных данных из класса](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=video&cd=1&cad=rja&uact=8&ved=0CB0QtwIwAA&url=http%3A%2F%2Fchannel9.msdn.com%2FShows%2FInside%2BWindows%2BPhone%2FIWP54--Windows-Phone-Data-Binding-and-the-Magic-of-XAML&ei=F1oHVNryM4ysogSJ2oDYDw&usg=AFQjCNEYvw1WA1rdF7bfpj5RwMLUs7RCVg).

 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [для объединения некоторых привязок данных с помощью Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="LiveWPF"></a> Отображение динамических данных в приложении WPF
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Создание источника данных XML](https://www.youtube.com/watch?v=RjQueappjqk&feature=youtube_gdata).

## <a name="LiveStore"></a> Отображение динамических данных в приложении Магазина или в приложении для телефона
 См. раздел [Работа с данными и файлами (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/br229562.aspx).

## <a name="see-also"></a>См. также раздел
 [Создание пользовательского интерфейса с помощью Blend для Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
