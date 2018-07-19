---
title: Использование модулей для включения файлов в решении | Документация Майкрософт
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
ms.openlocfilehash: f0773d9c167a0a799b7d9bc8ddd2b52afc9bc6f2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119436"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Использование модулей для включения файлов в решение
  Могут возникнуть ситуации, когда требуется развернуть файлы на сервер SharePoint, независимо от их типа, такие как главные страницы. Чтобы сделать это, можно использовать *модули* (не следует путать с [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] модули кода). Модули являются контейнерами для файлов в решении SharePoint. При развертывании решения, файлы в модуле копируются в указанные папки на сервере SharePoint.  
  
## <a name="module-items-and-elements"></a>Элементы модулей
 Чтобы создать модуль, добавьте его в проект, выбрав его в **Добавление нового элемента** диалоговое окно. Измените его *Elements.xml* файл, чтобы включить имена файлов, необходимо развернуть, где они находятся в системе, а они должны копироваться на сервере SharePoint.  
  
 Ниже приведен пример *Elements.xml* файл для модуля:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Только что созданный модули содержат следующие файлы по умолчанию:  
  
|Имя файла|Описание:|  
|---------------|-----------------|  
|*Elements.XML*|Файл определения модуля.|  
|*Sample.txt*|Файл-заполнитель, который служит в качестве примера файла в модуле.|  
  
 *Elements.xml* файл содержит следующие элементы:  
  
|Имя элемента|Описание:|  
|------------------|-----------------|  
|Элементы|Содержит все элементы, определенные в модуле.|  
|Module|Модуль элемент имеет один атрибут, *имя*, который задает имя модуля в формате `<Module Name="Module1">`.<br /><br /> Обратите внимание, что если вы изменяете имя модуля (или его *имя_папки* свойство), необходимо вручную обновить имя в элементе модуля.<br /><br /> Если указать вложенный каталог для файлов в элементе модуля [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) автоматически создаст для них соответствующую структуру каталогов.|  
|Файл|Элемент File имеет два параметра *путь* и *URL-адрес*.<br /><br /> -Path: Имя и расположение файла решения SharePoint. Следующий формат: `Path="Module1\Sample.txt"`.<br /><br /> -URL-адрес: Расположение, где этот файл будет развернут на сервере SharePoint. Следующий формат: `Url="Module1/Sample.txt"`.<br /><br /> -Type: Необязательный атрибут, имеет два параметра: *GhostableInLibrary* и *Ghostable*. Следующий формат: `Type="GhostableInLibrary"`. Указание *GhostableInLibrary* означает, что файл будет добавлен в библиотеку документов SharePoint вместе с элемент списка, сопровождающее файл при его добавлении в библиотеку. Указание *Ghostable* файл будет добавлен в SharePoint вне библиотеки документов.|  
  
 Каждый файл, который вы хотите развернуть требует отдельного `<File>` запись в элементе *Elements.xml*.  
  
## <a name="see-also"></a>См. также
 [Практическое: включение файлов с помощью модуля](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [Практическое: Подготовка файла](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
