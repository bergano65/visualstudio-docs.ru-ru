---
title: Защита документов в решениях уровня документа
description: Узнайте, как можно использовать функции защиты Microsoft Office Word и Microsoft Office Excel в проектах уровня документа.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ddfe9d70cafc6acf7526c8819cb9ae3f46ea8022
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910549"
---
# <a name="document-protection-in-document-level-solutions"></a>Защита документов в решениях уровня документа
  Функции защиты Microsoft Office Word и Microsoft Office Excel можно использовать в проектах уровня документа. Эти функции запрещают неавторизованным пользователям вносить изменения в защищенные части документа.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 С помощью Excel можно включить или отключить защиту, пока книга открыта в конструкторе. С помощью Word можно включить защиту только за пределами конструктора. Во время выполнения можно включить или отключить защиту программным способом как для Word, так и для Excel.

 Если защита документов включена для документа, открытого в конструкторе, все элементы управления удаляются из **панели элементов** или становятся недоступными, и из окна « **Источники данных** » в документ нельзя перетаскивать ничего.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument и защищенные документы
 Если документ защищен, доступ к кэшу данных извне этого документа невозможен. Нельзя использовать <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс для получения или обработки данных, кэшируемых в защищенном документе, или использовать другие методы <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса.

## <a name="word-document-protection-in-the-designer"></a>Защита документов Word в конструкторе
 Если вы добавляете защиту в документ или шаблон Word, когда он открыт в Visual Studio, вы не можете приступить к принудительной защите в конструкторе. Документ находится в режиме конструктора, пока он открыт в Visual Studio, и должен находиться в режиме выполнения, прежде чем можно будет приступить к включению защиты.

 Однако при создании проекта, использующего существующий документ Word с включенной защитой, документ будет защищен при открытии в конструкторе. Защищенные части документа изменить нельзя, но можно написать код в редакторе кода для автоматизации документа. Вы также не можете выполнить сборку проекта, если включена защита, а документ открыт в Visual Studio.

 Отключить защиту можно, пока документ открыт в конструкторе, чтобы можно было изменить документ и выполнить сборку проекта. Вы не можете отключить защиту для копии в конструкторе во время отладки. документ, который открывается во время отладки, представляет собой отдельную копию, открытую в конструкторе (выходная копия хранится в каталоге *\bin* для Visual Basic и каталог *\bin\Debug* для C#).

 Вы можете включить защиту копии документа, который открывается в конструкторе, закрыв проект в Visual Studio, открыв копию документа в каталоге проекта и включив защиту.

## <a name="enforce-word-document-protection-on-build"></a>Принудительно применять защиту документов Word при сборке
 Visual Studio применяет защиту для документов и шаблонов Word в процессе сборки, поэтому защита включается, когда документ открывается для отладки. Документ защищен пустым паролем.

 Защита включается во время сборки, поэтому если в событии документа есть код <xref:Microsoft.Office.Tools.Word.Document.Startup> , который может вызвать исключения или изменить поведение приложения, этот код можно правильно отладить. При включении защиты после открытия документа код инициализации не может быть отлажен или протестирован.

## <a name="setting-the-password"></a>Установка пароля
 Visual Studio автоматически включает защиту, но не предоставляет пароль по умолчанию. Если требуется, чтобы защита документа была защищена паролем, необходимо добавить ее перед развертыванием решения. Добавление пароля позволяет разрешить полномочным пользователям удалять защиту из документа. без пароля невозможно легко удалить защиту. Дополнительные сведения о настройке пароля см. в разделе Справка в конкретном приложении Office.

## <a name="see-also"></a>См. также раздел
- [Руководство. Программная защита документов и частей документов](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Обзор управления правами на информацию и расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)
- [Как разрешите выполнение кода для документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
