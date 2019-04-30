---
title: Практическое руководство. Открытие решений Office без выполнения кода
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 366416e4f18435bd01391657eb2fc4f65f8a4d62
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441765"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Практическое руководство. Открытие решений Office без выполнения кода
  Решения Microsoft Office, созданные с помощью расширений управляемого кода выполняется, даже если параметр безопасности в приложении Office конечного пользователя задан высокий приоритет. Это обусловлено безопасности кода сборки .NET управляется Microsoft .NET Framework, не по Microsoft Office.

 Однако бывают случаи, когда может потребоваться открыть документ без выполнения кода. Например код, который выполняется при открытии документа может привести к изменению содержимого, но вы хотите обновить внешний вид документа перед изменением кода его. Или может потребоваться отправить документ в ней другому пользователю, и не требуется код для запуска и возможно изменить содержимое.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Существует несколько способов открыть документ или книгу, содержащую расширения управляемого кода без выполнения кода сборки.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Чтобы обойти ее, удерживая нажатой клавишу Shift

- Открытие документов и книг из **файл** меню при нажатой **Shift** раздела для предотвращения удерживайте открыв документ Word и Excel.

    > [!NOTE]
    > При открытии документа или книги из **Приступая к работе** область задач, удерживая нажатой **Shift** защитит от выполнения кода. Кроме того удерживая нажатой клавишу SHIFT не запрещает события возникновение после открытия документа.

     Этот метод полезен в том случае, если вы хотите открыть документ для внесения изменений без выполнения кода и сначала изменение документа.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Обойти сборку, переименовав или удалив ее

- Если у вас есть необходимые разрешения на компьютере, где расположена сборка, можно переименовать или удалить сборку, чтобы документ или книгу не удается найти его. Это приводит к ошибке, возникшее при каждом открытии документа Office.

     Если решение используется несколькими людьми, этот метод предотвращает запуск для всех из них решения. Это может быть полезно, если обнаружена проблема в код или связанный сервер и вы хотите остановить все пользователи из его выполнения.

## <a name="see-also"></a>См. также
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
