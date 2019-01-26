---
title: Использовать файлы локальной базы данных в общие сведения о решений Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eec0a2adcb462bd2bb169cb997ce2fe352b0c72a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872707"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Использовать файлы локальной базы данных в общие сведения о решений Office
  Можно включить в файл базы данных, например SQL Server Express (*.mdf*) файла или Microsoft Office Access (*.mdb*) файл, в решении Office. Это позволяет конечным пользователям поддерживать локальной базы данных в ситуациях, когда к централизованной базе данных не требуется, например в локальной инвентаризации, который используется на одном компьютере.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>Импортировать файл базы данных в проект  
 Чтобы импортировать файл базы данных в проект, используйте **мастер настройки источника данных** для создания источника данных на основе файла базы данных. Мастер добавляет файл базы данных и типизированный набор данных в проект.  
  
## <a name="deploy-the-database-file"></a>Развернуть файл базы данных  
 **Мастер настройки источника данных** использует относительный путь для создания подключений к файлу локальной базы данных. Это позволяет копировать решение с одного компьютера на другой, если необходимо сохранить относительное расположение файлов.  
  
 Если развертывания решения на сервер, а затем распространить документ для каждого конечного пользователя, необходимо также вручную распространить файл базы данных и установить его в той же позиции относительно документа. Это означает, что конечный пользователь невозможно переместить документ в новое расположение на своем компьютере, если только он перемещает файл базы данных.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Файлы локальной базы данных и кэширование набора данных  
 В решениях уровня документа для Microsoft Office Excel и Microsoft Office Word, вы можете кэшировать наборов данных в документе, помечая экземпляра набора данных с атрибутом <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. При добавлении файла базы данных в проект с помощью **мастер настройки источника данных**, типизированный набор данных добавляется в проект автоматически. Редко бывает необходимо применить <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> в этот набор данных, так как данные являются локальными для компьютера пользователя. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Практическое руководство. Обновить источник данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Кэширование данных](../vsto/caching-data.md)  
