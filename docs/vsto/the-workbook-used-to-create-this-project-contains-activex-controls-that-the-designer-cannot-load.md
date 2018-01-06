---
title: "Книга, использованная для создания этого проекта содержит элементы управления ActiveX, которые не удается загрузить конструктор | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
ms.assetid: 91e9c6ee-7543-41e3-be0c-6c000cfd32d1
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2227af08d42b6cf47f7db4ba68e568b9e315bae6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Книга, использованная при создании данного проекта, содержит элемент управления ActiveX, который конструктору не удалось загрузить
  Эта ошибка возникает при добавлении элемента управления в документ Word или на лист Excel программным путем, сохранении документа или книги и последующем создании нового решения на уровне документа на основе этого документа или книги.  
  
 Данные, описывающие управляемый тип элемента управления, не сохраняются вместе с документом или книгой. При создании нового решения на основе этого документа или книги Visual Studio не будет иметь достаточно сведений для загрузки элемента управления в конструктор элемента узла.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Откройте документ или книгу.  
  
2.  Удалите элементы управления, добавленные во время выполнения. Это можно сделать, выбрав их в документе или книге и нажав клавишу DELETE.  
  
3.  Создайте решение на уровне документа на основе документа или книги.  
  
## <a name="see-also"></a>См. также  
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  