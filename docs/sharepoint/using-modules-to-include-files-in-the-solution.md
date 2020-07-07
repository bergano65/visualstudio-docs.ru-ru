---
title: Использование модулей для включения файлов в решение | Документация Майкрософт
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 778bbc9cff2d7853628edbb5be6466acc55d9ab8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015823"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Использование модулей для включения файлов в решение
  Иногда может потребоваться развернуть файлы на сервере SharePoint независимо от типа файлов, например новых главных страниц. Для этого можно использовать *модули* (не путать с [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] модулями кода). Модули — это контейнеры для файлов в решении SharePoint. При развертывании решения файлы в модуле копируются в указанные папки на сервере SharePoint.

## <a name="module-items-and-elements"></a>Элементы и элементы модуля
 Чтобы создать модуль, добавьте его в проект, выбрав его в диалоговом окне **Добавление нового элемента** . Затем измените его *Elements.xml* файл, включив в него имена файлов, которые требуется развернуть, где они находятся в системе и где они должны быть скопированы на сервере SharePoint.

 Ниже приведен пример файла *Elements.xml* для модуля:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Только что созданные модули содержат следующие файлы по умолчанию:

|Имя файла|Описание|
|---------------|-----------------|
|*Elements.xml*|Файл определения для модуля.|
|*Sample.txt*|Файл заполнителя, который служит примером файла в модуле.|

 Файл *Elements.xml* содержит следующие элементы:

|Имя элемента|Описание|
|------------------|-----------------|
|Элементы|Содержит все элементы, определенные в модуле.|
|Модуль|Элемент Module имеет единственный атрибут *Name*, который указывает имя модуля в формате `<Module Name="Module1">` .<br /><br /> Обратите внимание, что при изменении имени модуля (или свойства его *имени папки* ) необходимо вручную обновить имя в элементе Module.<br /><br /> Если указать подкаталог для файлов в элементе Module, то [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) автоматически создаст соответствующую структуру каталогов для них.|
|Файл|Элемент File имеет два параметра: *path* и *URL*.<br /><br /> -Path: имя и расположение файла в решении SharePoint. Формат:, `Path="Module1\Sample.txt"` .<br /><br /> -URL — расположение, в котором будет развернут файл на сервере SharePoint. Формат:, `Url="Module1/Sample.txt"` .<br /><br /> -Type: необязательный атрибут с двумя параметрами: *гхостаблеинлибрари* и *Ghost*. Формат:, `Type="GhostableInLibrary"` . Указание *гхостаблеинлибрари* означает, что файл будет добавлен в библиотеку документов SharePoint вместе с элементом списка, сопровождающим файл при его добавлении в библиотеку. Указание *фантомных* файлов приводит к добавлению файла в SharePoint за пределами библиотеки документов.|

 Для каждого файла, который требуется развернуть, требуется отдельная `<File>` запись элемента в *Elements.xml*.

## <a name="see-also"></a>См. также раздел
- [Инструкции. Включение файлов с помощью модуля](../sharepoint/how-to-include-files-by-using-a-module.md)
- [как подготавливать файл](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
