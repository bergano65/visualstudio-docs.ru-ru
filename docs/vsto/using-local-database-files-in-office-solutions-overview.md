---
title: Использовать файлы локальной базы данных в решений Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01e9dc3df93e1f721eba9ce3bcf65d4fb8bb1ca1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767586"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Использовать файлы локальной базы данных в решений Office
  Можно включить файл базы данных, таких как SQL Server Express (*.mdf*) файла или Microsoft Office Access (*.mdb*) файл в решении Office. Это позволяет конечному пользователю поддерживать локальную базу данных в ситуациях, где к централизованной базе данных не требуется, например в локальном инвентаризации решение, которое используется на одном компьютере.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>Импорт файла базы данных в проект  
 Чтобы импортировать файл базы данных в проект, используйте **мастер настройки источника данных** для создания источника данных на основе файла базы данных. Мастер добавит файл базы данных и типизированный набор данных в проект.  
  
## <a name="deploy-the-database-file"></a>Развертывание файла базы данных  
 **Мастер настройки источника данных** использует относительный путь для создания соединения с файлом локальной базы данных. Это позволяет копировать решение с одного компьютера на другой, если поддерживается относительное расположение файлов.  
  
 При развертывании решения на сервере и распространении документа для каждого конечного пользователя, необходимо также вручную распространить файл базы данных и установить его в той же позиции относительно документа. Это означает, что конечному пользователю не удается переместить документ в новое расположение на своем компьютере, если пользователь перемещает файл базы данных.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Файлы локальной базы данных и кэширование набора данных  
 В решениях уровня документа для Microsoft Office Excel и Microsoft Office Word, можно кэшировать наборов данных в документе маркировкой экземпляра набора данных с помощью атрибута <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. При добавлении файла базы данных в проект с помощью **мастер настройки источника данных**, типизированный набор данных добавляется в проект автоматически. Редко бывает необходимо применить <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> к этому набору данных, поскольку данные являются локальными для компьютера пользователя. Дополнительные сведения см. в разделе [данные кэша](../vsto/caching-data.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Как: Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Как: обновления источника данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Кэширование данных](../vsto/caching-data.md)  
  
  