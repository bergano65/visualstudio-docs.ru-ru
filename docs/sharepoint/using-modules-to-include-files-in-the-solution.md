---
title: Использование модулей для включения файлов в решении | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f9389e5928c74e5ee60bee90b375671777f1b807
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="using-modules-to-include-files-in-the-solution"></a>Использование модулей для включения файлов в решение
  Могут возникнуть ситуации, когда требуется развернуть файлы на сервере SharePoint, независимо от их типа, например главные страницы. Чтобы сделать это, можно использовать *модули* (не следует путать с [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] модули кода). Модули являются контейнерами для файлов решения SharePoint. При развертывании решения файлы в модуле копируются в указанные папки на сервере SharePoint.  
  
## <a name="module-items-and-elements"></a>Элементы модулей  
 Чтобы создать модуль, добавьте его в проект, выбрав его в **Добавление нового элемента** диалоговое окно. Затем измените его файл Elements.xml, чтобы включить имена файлов, которые требуется развернуть, где они находятся в системе, а они должны копироваться на сервере SharePoint.  
  
 Ниже приведен пример файла Elements.xml для модуля:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Новые модули содержат следующие файлы по умолчанию:  
  
|Имя файла|Описание|  
|---------------|-----------------|  
|Файл Elements.XML|Файл определения модуля.|  
|Sample.txt|Файл-заполнитель, который служит в качестве примера файла в модуле.|  
  
 Файл Elements.xml содержит следующие элементы:  
  
|Имя элемента|Описание|  
|------------------|-----------------|  
|Элементы|Содержит все элементы, определенные в модуле.|  
|Module|Модуль элемент имеет один атрибут, *имя*, указывающий имя модуля в формате `<Module Name="Module1">`.<br /><br /> Обратите внимание, что если изменить имя модуля (или его *имя папки* свойства), необходимо вручную обновить имя в элементе Module.<br /><br /> Если указать вложенный каталог для файлов в элементе Module [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) автоматически создаст соответствующую структуру каталогов для них.|  
|Файл|Элемент File имеет два параметра *путь* и *URL-адрес*.<br /><br /> -Path: Имя и расположение файла в решении SharePoint. Используется формат, `Path="Module1\Sample.txt"`.<br /><br /> -: Url-Адрес развертывания файла на сервере SharePoint. Используется формат, `Url="Module1/Sample.txt"`.<br /><br /> -Type: Необязательный атрибут, который имеет два параметра: *GhostableInLibrary* и *Ghostable*. Используется формат, `Type="GhostableInLibrary"`. Указание *GhostableInLibrary* означает файл будет добавлен в библиотеку документов SharePoint вместе с элемента списка, сопровождающее файла при добавлении в библиотеку. Указание *Ghostable* файл будет добавлен в SharePoint вне библиотеки документов.|  
  
 Каждый файл, который вы хотите развернуть необходим отдельный `<File>` записи элементов в Elements.xml.  
  
## <a name="see-also"></a>См. также  
 [Как: включаемых файлов с помощью модуля](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [как: подготовить файл](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  