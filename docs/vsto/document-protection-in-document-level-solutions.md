---
title: "Защита в решениях уровня документа документов | Документы Microsoft"
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
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cb0ccb9369c3430cf04e7e7c6b62335721e8005f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="document-protection-in-document-level-solutions"></a>Защита документов в решениях уровня документа
  Можно использовать функции защиты Microsoft Office Word и Microsoft Office Excel в проектах уровня документа. Эти функции блокируют несанкционированного внесения изменений в защищенные части документа.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 С помощью Excel, можно включить защиту и выключить пока книга открыта в конструкторе. Microsoft Word, можно включить защиту только вне конструктора. Во время выполнения можно включить или отключить защиту программными средствами для Word и Excel.  
  
 Если защита включена в документе, который открыт в конструкторе, все элементы управления будут удалены из **элементов** или становятся недоступными, и нельзя перетащить от **источники данных** окно документа.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument и защищенные документы  
 Если документ защищен, кэш данных нельзя получить доступ из вне документа. Нельзя использовать <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса для извлечения или управления данными, которые кэшируются в защищенном документе или использовать другие методы <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> класса.  
  
## <a name="word-document-protection-in-the-designer"></a>Защита документа Word в конструкторе  
 Если добавление защиты для документа Word или шаблона, когда он открыт в Visual Studio, не удалось запустить защиту в конструкторе. Документ находится в режиме конструктора, пока он открыт в Visual Studio, и он должен находиться в режиме выполнения, прежде чем включить защиту.  
  
 Тем не менее при создании проекта, использующего существующий документ Word с включенной защитой, документ защищен, открытой в конструкторе. Нельзя редактировать защищенные части документа, но можно писать код в редакторе кода для автоматизации документа. Также нельзя построить проект, если включена защита, когда документ открыт в Visual Studio.  
  
 Параметр можно выключить защиты, пока он открыт в конструкторе, можно изменить документ и постройте проект. Нельзя отключить защиту для копирования в конструкторе при отладке; документ, который открывается при отладке кода — это отдельный от одного открытого в конструкторе (Копировать выходные данные хранятся в каталоге \bin для Visual Basic и каталог \bin\debug для C#).  
  
 Можно включить защиту той копии документа, который откроется в конструкторе, закрыв проект в Visual Studio, открыть копию документа, который находится в каталоге проекта и включения защиты.  
  
## <a name="enforcing-word-document-protection-on-build"></a>Принудительная защита документа Word при построении  
 Visual Studio включает принудительную защиту для документов Word и шаблонов в процессе построения так, что защита включена, при открытии документа для отладки. Документ защищен пустым паролем.  
  
 Защита включается во время построения таким образом, при наличии кода в документе <xref:Microsoft.Office.Tools.Word.Document.Startup> событие, которое может вызвать исключение или изменить поведение приложения, этот код можно корректно отладить. При включении защиты после открытия документа, код инициализации нельзя отлаживать или протестировать.  
  
## <a name="setting-the-password"></a>Установка пароля  
 Visual Studio автоматически включает защиту, но не устанавливает пароль по умолчанию. Если требуется, чтобы документ был защищен паролем, необходимо добавить перед развертыванием решения. Добавление пароля позволяет авторизованным пользователям снять защиту с документа. без указания пароля не может легко удалить защиту. Дополнительные сведения об установке пароля см.  
  
## <a name="see-also"></a>См. также  
 [Как: программная Защита документов и их частей](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)   
 [Управление правами и Обзор расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Как: код разрешено выполнение с выделенным документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  