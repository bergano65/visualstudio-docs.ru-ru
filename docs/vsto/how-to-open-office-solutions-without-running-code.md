---
title: Как выполнить Открытие решений Office без выполнения кода
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7684fd2d01d0151798c9e59c593e3e0c2acb95b1
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646910"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Как выполнить Открытие решений Office без выполнения кода
  Решения Microsoft Office, созданные с помощью расширений управляемого кода выполняется, даже если параметр безопасности в приложении Office конечного пользователя задан высокий приоритет. Это обусловлено безопасности кода сборки .NET управляется Microsoft .NET Framework, не по Microsoft Office.  
  
 Однако бывают случаи, когда может потребоваться открыть документ без выполнения кода. Например код, который выполняется при открытии документа может привести к изменению содержимого, но вы хотите обновить внешний вид документа перед изменением кода его. Или может потребоваться отправить документ в ней другому пользователю, и не требуется код для запуска и возможно изменить содержимое.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Существует несколько способов открыть документ или книгу, содержащую расширения управляемого кода без выполнения кода сборки.  
  
## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Чтобы обойти ее, удерживая нажатой клавишу Shift  
  
-   Открытие документов и книг из **файл** меню при нажатой **Shift** раздела для предотвращения удерживайте открыв документ Word и Excel.  
  
    > [!NOTE]  
    >  При открытии документа или книги из **Приступая к работе** область задач, удерживая нажатой **Shift** защитит от выполнения кода. Кроме того удерживая нажатой клавишу SHIFT не запрещает события возникновение после открытия документа.  
  
     Этот метод полезен в том случае, если вы хотите открыть документ для внесения изменений без выполнения кода и сначала изменение документа.  
  
## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Обойти сборку, переименовав или удалив ее  
  
-   Если у вас есть необходимые разрешения на компьютере, где расположена сборка, можно переименовать или удалить сборку, чтобы документ или книгу не удается найти его. Это приводит к ошибке, возникшее при каждом открытии документа Office.  
  
     Если решение используется несколькими людьми, этот метод предотвращает запуск для всех из них решения. Это может быть полезно, если обнаружена проблема в код или связанный сервер и вы хотите остановить все пользователи из его выполнения.  
  
## <a name="see-also"></a>См. также  
 [Безопасные решения Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  