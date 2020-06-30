---
title: Руководство. Открытие решений Office без выполнения кода
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: d84515c2c3159b61b96f77555b23eef0df0ae961
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543485"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Руководство. Открытие решений Office без выполнения кода
  Microsoft Office решение, созданное с помощью расширений управляемого кода, выполняется, даже если параметр безопасности в приложении Office конечного пользователя имеет значение Высокий. Это обусловлено тем, что безопасность кода сборки .NET управляется платформой Microsoft .NET, а не Microsoft Office.

 Однако иногда требуется открыть документ без выполнения кода. Например, код, выполняемый при открытии документа, может изменить содержимое, но необходимо обновить способ, которым документ будет выглядеть перед тем, как код изменит его. Или вам может потребоваться отправить документ с определенными сведениями кому-то, и вы не хотите, чтобы код выполнялся и, возможно, мог изменить содержимое.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Существует несколько способов открыть документ или книгу, содержащую расширения управляемого кода, без выполнения кода сборки.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Обход сборки с помощью клавиши Shift

- Откройте документы и книги из меню **файл** , удерживая нажатой клавишу **SHIFT** , чтобы предотвратить возникновение в Word и Excel событий инициализации во время открытия документа.

    > [!NOTE]
    > При открытии документа или книги из области задач **Начало работы** при нажатой **клавише Shift** не выполняется обход кода. Кроме того, удерживание нажатой клавиши SHIFT не мешает порождению событий после открытия документа.

     Этот метод полезен, если необходимо открыть документ для внесения изменений без выполнения кода, а сначала изменить документ.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Обход сборки путем ее переименования или удаления

- Если у вас есть необходимые разрешения на компьютере, где находится сборка, можно переименовать или удалить сборку, чтобы документ или книга не могли его найти. Это приводит к возникновению ошибки при каждом открытии документа Office.

     Если решение используется несколькими людьми, этот метод предотвращает запуск решения для всех из них. Это может быть полезно в том случае, если проблема обнаружена в коде или на сервере, на который указывает ссылка, и вы хотите предотвратить его выполнение всеми пользователями.

## <a name="see-also"></a>См. также раздел
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Манифесты приложений и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
