---
title: Защита документов в решениях уровня документа
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6cc01c6506c4a3fca85029a8dcaf08607427ea4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596715"
---
# <a name="document-protection-in-document-level-solutions"></a>Защита документов в решениях уровня документа
  Можно использовать функции защиты Microsoft Office Word и Microsoft Office Excel в проектах уровня документа. Эти функции блокируются неавторизованные пользователи вносить изменения в защищенные части документа.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 С помощью Excel, можно включить защиту и отключать пока книга открыта в конструкторе. Microsoft Word, можно включить защиту только за пределами конструктора. Во время выполнения можно включить или отключить защиту программным образом для Word и Excel.

 При включении защиты документа в документе, который открыт в конструкторе, все элементы управления будут удалены из **элементов** или становятся недоступными, и вам не удается перетащить элементы из **источников данных** окно документа.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument и защищенные документы
 Если документ защищен, кэш данных недоступны из вне документа. Нельзя использовать <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса для извлечения или управления данными, которые кэшируются в защищенном документе, или используйте другие методы <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> класса.

## <a name="word-document-protection-in-the-designer"></a>Защита документов Word в конструкторе
 Если защита добавляется к документу Word или шаблона, когда он открыт в Visual Studio, не удалось запустить защиту в конструкторе. Документ находится в режиме конструктора, пока он открыт в Visual Studio, и он должен находиться в режиме выполнения, прежде чем включить защиту.

 Тем не менее если создается проект, использующий существующий документ Word с включенной защитой, документ защищен, открытой в конструкторе. Нельзя редактировать в защищенные части документа, но можно писать код в редакторе кода для автоматизации документа. Также не может построить проект, если включена защита, когда документ открыт в среде Visual Studio.

 Вы можете отключить защиты во время документ открыт в конструкторе, так что можно изменить документ и сборку проекта. Нельзя отключить защиту для копирования в конструкторе, в процессе отладки; документ, который открывается во время отладки — это отдельный экземпляр из тому, который открыт в конструкторе (Копировать выходные данные хранятся в *\bin* каталог в Visual Basic и *\bin\debug* каталог C# ).

 Вы можете включить защиту на копию документа, который откроется в конструкторе, завершение проекта в Visual Studio, открыть копию документа, который находится в каталоге проекта и включения защиты.

## <a name="enforce-word-document-protection-on-build"></a>Принудительная защита документа Word в построении
 Visual Studio запускает принудительную защиту для документов Word и шаблоны во время сборки, так что защита включена, при открытии документа для отладки. Документ защищен пустым паролем.

 Защита включается во время сборки таким образом, при наличии кода в документе <xref:Microsoft.Office.Tools.Word.Document.Startup> событие, которое может вызвать исключение или изменить поведение приложения, этот код можно корректно отладить. При включении защиты, после открытия документа, код инициализации нельзя отлаживать или протестировать.

## <a name="setting-the-password"></a>Установка пароля
 Visual Studio автоматически включает защиту, но не устанавливает пароль по умолчанию. Если требуется, чтобы документ был защищен паролем, необходимо добавить перед развертыванием решения. Добавление пароля позволяет авторизованные пользователи могут снять защиту с документа; без указания пароля невозможно легко удалить защиту. Дополнительные сведения о настройке пароля см.

## <a name="see-also"></a>См. также
- [Практическое руководство. Программная Защита документов и их частей](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)
- [Управление правами и общие сведения о расширениях управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Защита паролей в документах Office](../vsto/password-protection-on-office-documents.md)
- [Практическое руководство. Разрешить выполнения кода программной части документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
