---
title: Библиотека веб-элементов управления (управляемый код) | Документация Майкрософт
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
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031f894eb2e117a213f4f9fbbf08ac57a1512d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688166"
---
# <a name="web-control-library-managed-code"></a>Библиотека веб-элементов управления (управляемый код)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаблон проекта библиотеки веб-элементов управления позволяет создавать DLL-библиотеку. Поскольку библиотека классов представляет собой DLL, ее нельзя запускать напрямую. Необходимо создать страницу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], содержащую элемент управления. Дополнительные сведения см. в разделе [шаблон библиотеки веб-элементов управления](https://msdn.microsoft.com/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Для отладки библиотеки веб-элементов управления (Метод 1)  
  
1. Откройте существующий проект библиотеки веб-элементов управления или создайте новый.  
  
2. Создайте страницу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], содержащую элемент управления.  
  
3. На веб-узле, содержащем тестовую программу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], создайте подкаталог с именем `/Code`.  
  
4. Скопируйте исходный код элемента управления в подкаталог `/Code`.  
  
5. Откройте исходный код в подкаталоге `/Code` и установите точки останова.  
  
6. Откройте окно браузера с URL-адресом тестовой программы. Когда в элементе управления будет достигнута точка останова, можно будет начать отладку.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Отладка библиотеки веб-элементов управления (метод 2)  
  
1. Создайте проект ведущего приложения и проект веб-элемента управления в одном решении.  
  
2. В **Обозреватель решений**щелкните ведущее приложение правой кнопкой мыши и выберите команду **Добавить ссылку**.  
  
3. Добавьте ссылку на проект веб-элемента управления.  
  
## <a name="see-also"></a>См. также:  
 [Веб-приложения ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)
