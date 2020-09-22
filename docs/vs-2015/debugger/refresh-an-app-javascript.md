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
ms.openlocfilehash: b5b8be97212f4510002a78e6565fc9884930db89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842828"
---
# <a name="refresh-an-app-javascript"></a>Обновление приложения (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Применяется к Windows и Windows Phone] (.. /Video windows_and_phone_content.png "windows_and_phone_content")  
  
 Вы можете внести изменения в код во время отладки, а затем обновить приложение магазина с помощью JavaScript, нажав кнопку **обновить приложение Windows** на панели инструментов **Отладка** . Нажатие этой кнопки перезапускает приложение без остановки и перезапуска отладчика. Возможность обновления позволяет вносить изменения в код HTML, CSS и JavaScript и сразу видеть результат. Эта возможность поддерживается как для приложений Магазина Windows, так и для приложений Магазина Windows Phone.  
  
 Обновление не сохраняет состояние приложения и не отражает следующие изменения в приложении:  
  
- изменения в файле манифеста пакета, включая изменения изображений, указанных в манифесте пакета;  
  
- изменения ссылок, такие как добавление или удаление ссылки на SDK, и изменения в компонентах среды выполнения Windows (WINMD-файлах);  
  
- изменения ресурсов, такие как изменения в строках в RESJSON-файлах;  
  
- изменения в файлах проекта, приводящие к изменению путей к файлам, появлению новых файлов проекта или удалению файлов;  
  
- изменения свойств проекта и элементов, такие как изменения выбранного устройства отладки или изменения действия пакета для файла (в окне "Свойства").  
  
> [!IMPORTANT]
> При изменении ссылок, манифеста пакета или при внесении других изменений из списка выше необходимо остановить и перезапустить отладчик для обновления файлов с исходным кодом HTML, CSS и JavaScript.  
  
### <a name="to-refresh-an-app"></a>Обновление приложения  
  
1. Создайте в Visual Studio новый проект, используя шаблон проекта "Приложение навигации".  
  
     Это может быть приложение Магазина Windows, приложение Магазина Windows Phone или универсальное приложение.  
  
2. Открыв шаблон в Visual Studio, выберите целевой объект отладки.  
  
     Если вашим текущим запускаемым проектом является проект Windows Phone, выберите эмулятор Windows Phone для цели отладки. В противном случае выберите **симулятор** или **локальный компьютер**.  
  
     ![Список для выбора целевого объекта отладки](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3. Нажмите клавишу F5, чтобы запустить приложение в режиме отладки.  
  
4. Перейдите в Visual Studio. (Нажмите F12.)  
  
5. В **Обозреватель решений**в **pages**  >  **корневой** папке страницы откройте home.html.  
  
6. Измените текст заголовка страницы с  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     на что-либо другое, например:  
  
    ```html  
    Hello!  
    ```  
  
7. Нажмите кнопку **Обновить приложение Windows**, которая выглядит следующим образом: ![Кнопка обновления приложения Windows](../debugger/media/js-refresh.png "JS_Refresh"). (Или нажмите клавишу F4.)  
  
8. Перейдите в приложение. Приложение перезапускается без перезапуска отладчика, и отображается новый заголовок.  
  
## <a name="see-also"></a>См. также:  
 [Краткое руководство. Отладка HTML и CSS](../debugger/quickstart-debug-html-and-css.md)
