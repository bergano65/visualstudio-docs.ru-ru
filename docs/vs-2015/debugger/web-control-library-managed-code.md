---
title: Веб-Библиотека элементов управления (управляемый код) | Документация Майкрософт
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
ms.openlocfilehash: 18f6e72d18154f11866671a3e448d88c91768c7f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047102"
---
# <a name="web-control-library-managed-code"></a>Библиотека веб-элементов управления (управляемый код)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаблон проекта библиотеки веб-элементов управления позволяет создавать DLL-библиотеку. Поскольку библиотека классов представляет собой DLL, ее нельзя запускать напрямую. Необходимо создать страницу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], содержащую элемент управления. Дополнительные сведения см. в разделе [Web Control Library Template](http://msdn.microsoft.com/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Для отладки библиотеки веб-элементов управления (Метод 1)  
  
1. Откройте существующий проект библиотеки веб-элементов управления или создайте новый.  
  
2. Создайте страницу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], содержащую элемент управления.  
  
3. На веб-узле, содержащем тестовую программу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], создайте подкаталог с именем `/Code`.  
  
4. Скопируйте исходный код элемента управления в подкаталог `/Code`.  
  
5. Откройте исходный код в подкаталоге `/Code` и установите точки останова.  
  
6. Откройте окно браузера с URL-адресом тестовой программы. Когда в элементе управления будет достигнута точка останова, можно будет начать отладку.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Отладка библиотеки элементов управления Web (метод 2)  
  
1. Создайте проект ведущего приложения и проект веб-элемента управления в одном решении.  
  
2. В **обозревателе решений**, щелкните правой кнопкой мыши ведущее приложение и выберите пункт **добавить ссылку**.  
  
3. Добавьте ссылку на проект веб-элемента управления.  
  
## <a name="see-also"></a>См. также  
 [Веб-приложения ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)
