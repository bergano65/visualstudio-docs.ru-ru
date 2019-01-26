---
title: Как выполнить Включение файлов с помощью модуля | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c08e04dd6ca95e691c33ce77bdedf6a655ee5b4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871732"
---
# <a name="how-to-include-files-by-using-a-module"></a>Как выполнить Включение файлов с помощью модуля
  *Модули* (не следует путать с [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] модули) представляют собой контейнеры, которые позволяют развертывать образы, текстовые файлы или файлы, такие как главные страницы ASPX в SharePoint.  
  
 Вы можете развернуть файл в библиотеку документов или как обычный файл (например default.aspx) вне библиотеки документов. Чтобы добавить файл в библиотеку документов, укажите `Type="GhostableInLibrary"` в качестве атрибута **файл** элемент. Этот параметр предписывает создавать элемент списка, чтобы перейти с файлом, при добавлении в библиотеку SharePoint. Чтобы развернуть файл вне библиотеки документов, укажите `Type="Ghostable"` или просто опустив **тип** атрибута.  
  
## <a name="add-a-module-to-a-sharepoint-solution"></a>Добавить модуль в решение SharePoint  
  
#### <a name="to-add-a-module"></a>Чтобы добавить модуль  
  
1.  Откройте или создайте проект SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
     Дополнительные сведения см. в разделе [SharePoint проект и проект шаблоны элементов](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  В **обозревателе решений**, выберите узел проекта и затем в строке меню выберите **проекта** > **Добавление нового элемента**.  
  
     Откроется диалоговое окно **Добавление нового элемента**.  
  
3.  В списке шаблонов SharePoint выберите **модуль** шаблона, а затем выберите **добавить** кнопки.  
  
     На этом этапе в проекте будет создан новый узел с именем Module1.  
  
4.  В узле Module1 удалите *Sample.txt* файл.  
  
     Sample.txt включается во всех новых модулях в качестве примера и не требуется. (Обратите внимание, что при удалении файла также удаляется его запись из модуля *Elements.xml* файл.)  
  
5.  Если требуется, чтобы файлы для развертывания в определенной структуре папок в SharePoint, создайте эти папки в узле Module1 в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , выбрав узел Module1, а затем в строке меню выберите **проекта**, **New Папка**.  
  
6.  Выберите папку, в которой вы хотите добавить файл и затем в строке меню выберите **проекта**, **добавить существующий элемент**.  
  
7.  Выберите один или несколько файлов, которые вы хотите развернуть в SharePoint, а затем выберите **добавить** кнопки.  
  
     При добавлении файла в проект, его запись автоматически добавляется в файл Elements.xml модуля. При развертывании проекта, файлы копируются на сервер SharePoint, относительно корневого каталога проекта, который задается путем **файл** элемента **URL-адрес** атрибут, например `Url="Module1/New Folder/SomeFile.doc`. Если вы хотите изменить место развертывания для файла, либо переместите его в другую папку в **обозревателе решений** или изменить его **URL-адрес** параметр.  
  
8.  Все файлы, которые нужно отобразить в библиотеке документов, добавьте `Type="GhostableInLibrary"` к их записи в атрибут *Elements.xml*. Например, примененная к объекту директива  
  
    ```xml  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Развертывание проекта.  
  
     Скопируйте файлы в указанных расположениях в SharePoint.  
  
## <a name="see-also"></a>См. также
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
