---
title: "Кроссплатформенная разработка для мобильных устройств | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: bc384c12-fccc-45d7-9fb9-b90d536aa663
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: xplat-cplusplus
ms.openlocfilehash: 030fe898926c1e1d124a780c9ba73fec31109cd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="cross-platform-mobile-development-examples"></a>Примеры разработки кроссплатформенных мобильных приложений
Несколько шаблонов, устанавливаемых компонентом Visual C++ для разработки кроссплатформенных мобильных приложений, создают полноценные примеры, которые можно использовать для обучения. Кроме того, в Центре разработки для Windows есть несколько примеров приложений, которые можно скачать и испытать в Visual Studio.  
  
-   [Пример приложения hello-jni для Android](https://code.msdn.microsoft.com/hello-jni-Android-790ab73d)  
  
     Этот пример представляет собой приложение hello-jni, перенесенное из Android NDK. В нем демонстрируется полностью готовое приложение Java Native Interface в стиле Hello World. Оно загружает строку из собственного метода, реализованного в общей библиотеке, а затем выводит ее на экран.  
  
-   [Пример приложения hello-gl2 для Android](https://code.msdn.microsoft.com/hello-gl2-Android-3b61896c)  
  
     Этот пример представляет собой приложение hello-gl2, перенесенное из Android NDK. В нем демонстрируется полностью готовое приложение Native Interface Android на основе OpenGL. В нем отрисовывается треугольник с помощью API шейдеров OpenGL ES 2.0.  
  
-   [Пример приложения Bitmap Plasma для Android](https://code.msdn.microsoft.com/Bitmap-Plasma-Android-77ae296a)  
  
     Этот пример представляет собой приложение Bitmap Plasma, перенесенное из Android NDK. В нем демонстрируется полностью готовое приложение Java Native Interface для Android на основе OpenGL ES 2.0. С его помощью показано, как напрямую работать с буферами растровых пикселей Android для создания эффекта плазмы.  
  
-   [Пример библиотеки TwoLibs для Android](https://code.msdn.microsoft.com/TwoLibs-Android-Library-6396e5c4)  
  
     Этот пример представляет собой образец библиотеки TwoLibs, перенесенный из Android NDK. В нем используется как динамически загружаемая общая библиотека, так и статическая собственная библиотека Android на C++, которая реализует метод, вызываемый из приложения Java Native Interface. Этот пример является хорошей отправной точкой, позволяющей разработчикам понять, как использовать статические и динамические общие библиотеки для создания полностью готового приложения JNI для Android с помощью Visual Studio 2015.  
  
-   [Пример приложения Tea Pot для Android](https://code.msdn.microsoft.com/Tea-Pot-Android-Application-e7c05d73)  
  
     Этот пример представляет собой приложение TeaPot, перенесенное из Android NDK. В нем демонстрируется полностью готовое приложение Java Native Interface для Android на основе OpenGL ES 2.0.  
  
-   [Пример приложения MoreTeaPots для Android](https://code.msdn.microsoft.com/MoreTeaPots-Android-a9bd8549)  
  
     Этот пример представляет собой приложение MoreTeaPots, перенесенное из Android NDK. В нем демонстрируется полностью готовое приложение Java Native Interface для Android на основе OpenGL.  
  
-   [Пример библиотеки test-libstdcpp для Android](https://code.msdn.microsoft.com/test-libstdcpp-Android-00b548f5)  
  
     Этот пример представляет собой образец библиотеки test-libstdc++, перенесенной из Android NDK и предназначенной специально для использования с Visual Studio 2015. Этот пример является хорошей отправной точкой, позволяющей разработчикам понять, как использовать стандартную библиотеку.  
  
 Чтобы открыть один из примеров в Visual Studio, скачайте ZIP-файл и откройте страницу **Свойства** этого файла в проводнике. Нажмите кнопку **Разблокировать** , а затем кнопку **ОК**. Извлеките содержимое ZIP-файла в удобное место, откройте папку C++ в извлеченном образце, а затем откройте файл решения.  
  
 Чтобы выполнить сборку образца, нажмите клавишу F7 или выберите в строке меню **Сборка**&gt; **Собрать решение**.