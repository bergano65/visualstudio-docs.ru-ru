---
title: "Как: открытие решений Office без выполнения кода | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c190c4ace56b2be9c63c9f11570354cddc6c8635
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Практическое руководство. Открытие решений Office без выполнения кода
  Решение Microsoft Office, созданные с помощью расширений управляемого кода выполняется, даже если установлен высокий параметр безопасности в приложении Office конечного пользователя. Это происходит потому безопасности кода сборки .NET управляется Microsoft .NET Framework и не по Microsoft Office.  
  
 Однако бывают случаи, когда может потребоваться открыть документ без выполнения кода. Например код, который выполняется при открытии документа может привести к изменению содержимого, но вы хотите обновить внешний вид документа до изменения кода он. Отправка документа с определенной информации в нем кто-то может потребоваться и код для выполнения и возможно изменить содержимое не следует.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Существует несколько способов, чтобы открыть документ или книгу, содержащую расширения управляемого кода без выполнения кода сборки.  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Обойти сборку с помощью клавиши SHIFT  
  
-   При открытии документа или книги из **файл** меню, удерживая нажатой клавишу SHIFT, чтобы предотвратить удерживайте Открытие документа Word и Excel.  
  
    > [!NOTE]  
    >  При открытии документа или книги из **Приступая к работе** область задач, удерживая нажатой клавишу SHIFT не защитит от выполнения кода. Кроме того удерживая нажатой клавишу SHIFT не запрещает события возникшее после открытия документа.  
  
     Этот метод полезен, если вы хотите открыть документ для внесения изменений без выполнения кода и начального изменения документа сначала.  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Обойти сборку, переименовав или удалив ее  
  
-   При наличии необходимых разрешений на компьютере, где расположена сборка можно переименовать или удалить сборку, документ или книгу не удается найти. Это приводит к ошибке возникла каждый раз при открытии документа Office.  
  
     Если решение используется несколькими пользователями, этот метод запрещает решения для всех из них. Это может быть полезно, если обнаружена проблема в коде или связанный сервер, и вы хотите остановить все пользователи из его выполнения.  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  