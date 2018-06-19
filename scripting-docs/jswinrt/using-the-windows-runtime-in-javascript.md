---
title: Использование среды выполнения Windows в JavaScript | Документы Майкрософт
ms.custom: ''
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571464"
---
# <a name="using-the-windows-runtime-in-javascript"></a>Использование среды выполнения Windows в JavaScript
При создании приложения универсальной платформы Windows вы можете использовать классы, методы и свойства среды выполнения Windows, что во многом аналогично тому, как использовали бы собственные объекты, методы и свойства JavaScript. Данный раздел содержит вводные сведения и ссылки на разделы, где поясняются базовые концепции использования API среды выполнения Windows в JavaScript, включая описание представления типов среды выполнения Windows, использования асинхронных методов среды выполнения Windows, а также ожидания возникновения и обработки событий среды выполнения Windows.  
  
 См. справочную документацию по языку [JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Компоненты среды выполнения Windows недоступны тем приложениям, которые выполняются в Internet Explorer.  
  
## <a name="windows-runtime-reference-documentation"></a>Справочная документация среды выполнения Windows  
 См. справочную документацию по [среде выполнения Windows](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx). Примеры кода доступны как на языке JavaScript, так и на языках C++, C# и Visual Basic.  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>Создание компонентов среды выполнения Windows на C++, C# или Visual Basic  
 Инструкции и рекомендации по созданию компонентов среды выполнения Windows, которые можно использовать в JavaScript, см. в разделах [Создание компонентов среды выполнения Windows в C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) и [Создание компонентов среды выполнения Windows в C# и Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Соглашения об использовании прописных или строчных букв для компонентов среды выполнения Windows  
 Соглашения об использовании прописных или строчных букв для компонентов среды выполнения Windows в JavaScript немного отличаются от аналогичных соглашений в других языках:  
  
-   Пространства имен и классы указываются в стиле Pascal:  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Члены классов, включая методы и свойства, и члены структур и перечислений указываются в "верблюжьем" стиле:  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Имена событий указываются в нижнем регистре:  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>См. также  
 [Рекомендации по использованию API среды выполнения Windows](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Использование асинхронных методов среды выполнения Windows](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Обработка событий среды выполнения Windows на языке JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Представление типов среды выполнения Windows в JavaScript](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Проекция JavaScript для DateTime и TimeSpan среды выполнения Windows](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)