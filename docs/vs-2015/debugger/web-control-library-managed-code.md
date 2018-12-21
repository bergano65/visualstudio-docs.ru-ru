---
title: Веб-Библиотека элементов управления (управляемый код) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: a523d593b4c61a7ca730cc60a6ed22a1be541f9c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807599"
---
# <a name="web-control-library-managed-code"></a>Библиотека веб-элементов управления (управляемый код)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаблон проекта библиотеки веб-элементов управления позволяет создавать DLL-библиотеку. Поскольку библиотека классов представляет собой DLL, ее нельзя запускать напрямую. Необходимо создать страницу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], содержащую элемент управления. Дополнительные сведения см. в разделе [Web Control Library Template](http://msdn.microsoft.com/en-us/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Для отладки библиотеки веб-элементов управления (Метод 1)  
  
1.  Откройте существующий проект библиотеки веб-элементов управления или создайте новый.  
  
2.  Создайте страницу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], содержащую элемент управления.  
  
3.  На веб-узле, содержащем тестовую программу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], создайте подкаталог с именем `/Code`.  
  
4.  Скопируйте исходный код элемента управления в подкаталог `/Code`.  
  
5.  Откройте исходный код в подкаталоге `/Code` и установите точки останова.  
  
6.  Откройте окно браузера с URL-адресом тестовой программы. Когда в элементе управления будет достигнута точка останова, можно будет начать отладку.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Отладка библиотеки элементов управления Web (метод 2)  
  
1.  Создайте проект ведущего приложения и проект веб-элемента управления в одном решении.  
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши ведущее приложение и выберите пункт **добавить ссылку**.  
  
3.  Добавьте ссылку на проект веб-элемента управления.  
  
## <a name="see-also"></a>См. также  
 [Веб-приложения ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)



