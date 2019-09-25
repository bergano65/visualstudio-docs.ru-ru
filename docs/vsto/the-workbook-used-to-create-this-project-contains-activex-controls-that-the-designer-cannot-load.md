---
title: Книга, использованная при создании данного проекта, содержит элемент управления ActiveX, который конструктору не удалось загрузить
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 27feb1c6a85740d8a9287ce3a2a47800595e178a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253779"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Книга, использованная при создании данного проекта, содержит элемент управления ActiveX, который конструктору не удалось загрузить
  Эта ошибка возникает при добавлении элемента управления в документ Word или на лист Excel программным путем, сохранении документа или книги и последующем создании нового решения на уровне документа на основе этого документа или книги.

 Данные, описывающие управляемый тип элемента управления, не сохраняются вместе с документом или книгой. При создании нового решения на основе этого документа или книги Visual Studio не будет иметь достаточно сведений для загрузки элемента управления в конструктор элемента узла.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Откройте документ или книгу.

2. Удалите элементы управления, добавленные во время выполнения. Это можно сделать, выбрав их в документе или книге и нажав клавишу **Delete** .

3. Создайте решение на уровне документа на основе документа или книги.

## <a name="see-also"></a>См. также
- [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
