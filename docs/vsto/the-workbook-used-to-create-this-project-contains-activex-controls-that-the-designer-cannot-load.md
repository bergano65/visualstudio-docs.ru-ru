---
title: Книга, использованная при создании данного проекта, содержит элемент управления ActiveX, который конструктору не удалось загрузить
ms.date: 02/02/2017
ms.topic: error-reference
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
ms.openlocfilehash: 4485489b48c4d1b03b608c6072cfc859e8bc8f59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537349"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Книга, использованная при создании данного проекта, содержит элемент управления ActiveX, который конструктору не удалось загрузить
  Эта ошибка возникает при добавлении элемента управления в документ Word или на лист Excel программным путем, сохранении документа или книги и последующем создании нового решения на уровне документа на основе этого документа или книги.

 Данные, описывающие управляемый тип элемента управления, не сохраняются вместе с документом или книгой. При создании нового решения на основе этого документа или книги Visual Studio не будет иметь достаточно сведений для загрузки элемента управления в конструктор элемента узла.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Откройте документ или книгу.

2. Удалите элементы управления, добавленные во время выполнения. Это можно сделать, выбрав их в документе или книге и нажав клавишу **Delete** .

3. Создайте решение на уровне документа на основе документа или книги.

## <a name="see-also"></a>См. также раздел
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
