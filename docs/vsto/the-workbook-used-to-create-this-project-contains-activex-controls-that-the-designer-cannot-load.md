---
title: Книга, использованная при создании данного проекта, содержит элемент управления ActiveX, который конструктору не удалось загрузить
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a48cff6b3d2e2b4a090ee5ec5cd879b272593cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876436"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Книга, использованная при создании данного проекта, содержит элемент управления ActiveX, который конструктору не удалось загрузить
  Эта ошибка возникает при добавлении элемента управления в документ Word или на лист Excel программным путем, сохранении документа или книги и последующем создании нового решения на уровне документа на основе этого документа или книги.  
  
 Данные, описывающие управляемый тип элемента управления, не сохраняются вместе с документом или книгой. При создании нового решения на основе этого документа или книги Visual Studio не будет иметь достаточно сведений для загрузки элемента управления в конструктор элемента узла.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Откройте документ или книгу.  
  
2.  Удалите элементы управления, которые были добавлены во время выполнения. Это можно сделать, выбрав их в документе или книге и нажав клавишу **удалить** ключ.  
  
3.  Создайте решение на уровне документа на основе документа или книги.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)  
