---
title: Книга содержит элементы ActiveX, которые невозможно загрузить
description: Узнайте, как устранить ошибку, возникающую, если книга содержит элементы управления ActiveX, которые невозможно загрузить.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: 7257e3940af72f344906642adc51a1dd98cb3f25
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524181"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>Книга содержит элементы ActiveX, которые невозможно загрузить

  Ошибка "книга, используемая для создания этого проекта содержит элементы управления ActiveX, которые конструктор не может загрузить" появляется при программном добавлении элемента управления в документ Word или на лист Excel, сохранении документа или книги, а также при создании нового решения на уровне документа на основе документа или книги.

 Данные, описывающие управляемый тип элемента управления, не сохраняются вместе с документом или книгой. При создании нового решения на основе этого документа или книги Visual Studio не будет иметь достаточно сведений для загрузки элемента управления в конструктор элемента узла.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Откройте документ или книгу.

2. Удалите элементы управления, добавленные во время выполнения. Это можно сделать, выбрав их в документе или книге и нажав клавишу **Delete** .

3. Создайте решение на уровне документа на основе документа или книги.

## <a name="see-also"></a>См. также раздел
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
