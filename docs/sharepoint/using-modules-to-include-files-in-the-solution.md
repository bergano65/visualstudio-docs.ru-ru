---
title: Использование модулей для включения файлов в решение | Документация Майкрософт
description: Чтобы развернуть файлы на сервере SharePoint, независимо от типа файлов (например, главные страницы), используйте модули или контейнеры для файлов в решении SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 86aea9800d0eaad4c36d5598e52dd7a35f3a7534
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892181"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Использование модулей для включения файлов в решение
  Вам может потребоваться развернуть файлы на сервере SharePoint независимо от их типа, например новые эталонные страницы. Для этого можно использовать *модули* (не путайте их с модулями кода [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]). Модули — это контейнеры для файлов в решении SharePoint. При развертывании решения файлы из модуля копируются в указанные папки на сервере SharePoint.

## <a name="module-items-and-elements"></a>Элементы модулей
 Чтобы создать модуль, добавьте его в проект, выбрав его в диалоговом окне **Добавление нового элемента**. Затем измените его файл *Elements.xml*, чтобы включить в него имена файлов, которые нужно развернуть, их расположение в системе и место на сервере SharePoint, куда они должны копироваться.

 Ниже приведен пример файла *Elements.xml* для модуля.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Новые модули содержат следующие файлы по умолчанию.

|Имя файла|Описание|
|---------------|-----------------|
|*Elements.xml*|Файл определения для модуля.|
|*Sample.txt*|Файл-прототип, служащий в качестве примера файла в модуле.|

 Файл *Elements.xml* содержит следующие элементы.

|Имя элемента|Описание|
|------------------|-----------------|
|Элементы|Содержит все элементы, определенные в модуле.|
|Модуль|Элемент Module имеет единственный атрибут *Name* (Имя), который задает имя модуля в формате `<Module Name="Module1">`.<br /><br /> Обратите внимание, что если вы изменяете имя модуля (или его свойство *Имя папки*), необходимо вручную обновить это имя в элементе Module.<br /><br /> Если вы указываете подкаталог для файлов в элементе Module, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) будет автоматически создавать для них соответствующую структуру каталогов.|
|Файл|Элемент File имеет два параметра, *Path* (Путь) и *Url* (URL-адрес).<br /><br /> — Path (Путь): имя и расположение файла в решении SharePoint. Формат: `Path="Module1\Sample.txt"`.<br /><br /> — Url (URL-адрес): расположение, в котором будет развернут этот файл на сервере SharePoint. Формат: `Url="Module1/Sample.txt"`.<br /><br /> — Type (Тип): необязательный атрибут, который может иметь одно из двух значений, *GhostableInLibrary* или *Ghostable*. Формат: `Type="GhostableInLibrary"`. При выборе значения *GhostableInLibrary* файл будет добавлен в библиотеку документов в SharePoint вместе с элементом списка, который сопровождает этот файл при добавлении в библиотеку. При выборе значения *Ghostable* файл будет добавлен в SharePoint вне библиотеки документов.|

 Для каждого файла, который вы хотите развернуть, требуется отдельная запись элемента `<File>` в файле *Elements.xml*.

## <a name="see-also"></a>См. также раздел
- [Практическое руководство. Включение файлов с помощью модуля](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Практическое руководство. Подготовка файла](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
