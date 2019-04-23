---
title: Обновление приложения (JavaScript) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e55e108901d9be62531e459f2b7805f86cfe6a08
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040645"
---
# <a name="refresh-an-app-javascript"></a>Обновление приложения (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Применяется к Windows и Windows Phone] (.. /Image/windows_and_phone_content.PNG «windows_and_phone_content»)  
  
 Внесения изменений в код во время отладки, а затем обновите app Store, с использованием JavaScript, нажав **обновить Windows приложение** , нажмите кнопку **Отладка** панели инструментов. Нажатие этой кнопки перезапускает приложение без остановки и перезапуска отладчика. Возможность обновления позволяет вносить изменения в код HTML, CSS и JavaScript и сразу видеть результат. Эта возможность поддерживается как для приложений Магазина Windows, так и для приложений Магазина Windows Phone.  
  
 Обновление не сохраняет состояние приложения и не отражает следующие изменения в приложении:  
  
- изменения в файле манифеста пакета, включая изменения изображений, указанных в манифесте пакета;  
  
- изменения ссылок, такие как добавление или удаление ссылки на SDK, и изменения в компонентах среды выполнения Windows (WINMD-файлах);  
  
- изменения ресурсов, такие как изменения в строках в RESJSON-файлах;  
  
- изменения в файлах проекта, приводящие к изменению путей к файлам, появлению новых файлов проекта или удалению файлов;  
  
- изменения свойств проекта и элементов, такие как изменения выбранного устройства отладки или изменения действия пакета для файла (в окне "Свойства").  
  
> [!IMPORTANT]
>  При изменении ссылок, манифеста пакета или при внесении других изменений из списка выше необходимо остановить и перезапустить отладчик для обновления файлов с исходным кодом HTML, CSS и JavaScript.  
  
### <a name="to-refresh-an-app"></a>Обновление приложения  
  
1. Создайте в Visual Studio новый проект, используя шаблон проекта "Приложение навигации".  
  
     Это может быть приложение Магазина Windows, приложение Магазина Windows Phone или универсальное приложение.  
  
2. Открыв шаблон в Visual Studio, выберите целевой объект отладки.  
  
     Если вашим текущим запускаемым проектом является проект Windows Phone, выберите эмулятор Windows Phone для цели отладки. В противном случае выберите **симулятор** или **локальный компьютер**.  
  
     ![Список целевых объектов отладки выберите](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3. Нажмите клавишу F5, чтобы запустить приложение в режиме отладки.  
  
4. Перейдите в Visual Studio. (Нажмите F12.)  
  
5. В **обозревателе решений**в **страниц** > **домашней** папку, откройте файл home.html.  
  
6. Измените текст заголовка страницы с  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     на что-либо другое, например:  
  
    ```html  
    Hello!  
    ```  
  
7. Нажмите кнопку **обновить Windows приложение** кнопку, которая выглядит следующим образом: ![Кнопка приложения Windows "Обновить"](../debugger/media/js-refresh.png "JS_Refresh"). (Или нажмите клавишу F4.)  
  
8. Перейдите в приложение. Приложение перезапускается без перезапуска отладчика, и отображается новый заголовок.  
  
## <a name="see-also"></a>См. также  
 [Краткое руководство. Отладка HTML и CSS](../debugger/quickstart-debug-html-and-css.md)
