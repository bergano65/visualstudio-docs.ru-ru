---
title: Инструкции. Включение файлов с помощью модуля | Документация Майкрософт
description: Сведения о включении файлов с помощью модуля, который представляет собой контейнер, позволяющий развертывать такие файлы, как главные страницы ASPX, текстовые файлы или изображения, в SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e83a1474c7dfe6385c36cc13646bfe40fc897640
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913629"
---
# <a name="how-to-include-files-by-using-a-module"></a>Практическое руководство. Включение файлов с помощью модуля
  *Модули* (не путать с [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] модулями) — это контейнеры, позволяющие развертывать в SharePoint файлы, такие как главные страницы ASPX, текстовые файлы или изображения.

 Можно выбрать развертывание файла в библиотеке документов или в виде обычного файла (например, Default. aspx) вне библиотеки документов. Чтобы добавить файл в библиотеку документов, укажите `Type="GhostableInLibrary"` в качестве атрибута в элементе **File** . Этот параметр указывает SharePoint создать элемент списка для добавления к файлу при его добавлении в библиотеку. Чтобы развернуть файл вне библиотеки документов, укажите `Type="Ghostable"` или просто опустите атрибут **Type** .

## <a name="add-a-module-to-a-sharepoint-solution"></a>Добавление модуля в решение SharePoint

#### <a name="to-add-a-module"></a>Добавление модуля

1. Откройте или создайте проект SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

     Дополнительные сведения см. в разделе [проект SharePoint и шаблоны элементов проектов](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. В **Обозреватель решений** выберите узел проекта, а затем в строке меню выберите **проект**  >  **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

3. В списке шаблонов SharePoint выберите шаблон **модуля** , а затем нажмите кнопку **Добавить** .

     На этом этапе в проекте будет создан новый узел с именем Module1.

4. В разделе Module1 удалите файл *Sample.txt* .

     Sample.txt входит во все новые модули в качестве примера и не требуется. (Обратите внимание, что при удалении файла также удаляется его запись из файла *Elements.xml* модуля.)

5. Если вы хотите, чтобы файлы развертывались в определенной структуре папок в SharePoint, создайте эти папки в разделе Module1 в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , выбрав узел Module1, а затем в строке меню выберите **проект**, **создать папку**.

6. Выберите папку, в которую нужно добавить файл, а затем в строке меню выберите **проект**, **Добавить существующий элемент**.

7. Выберите один или несколько файлов, которые требуется развернуть в SharePoint, а затем нажмите кнопку **Добавить** .

     При добавлении файла в проект запись для него автоматически добавляется в файл Elements.xml модуля. При развертывании проекта файлы копируются на сервер SharePoint Server относительно корневого каталога проекта, который задается атрибутом **URL-адреса** элемента **File** , например `Url="Module1/New Folder/SomeFile.doc` . Если вы хотите изменить расположение развертывания для файла, переместите его в другую папку в **Обозреватель решений** или измените его **URL-адрес** .

8. Для файлов, которые должны отображаться в библиотеке документов, добавьте `Type="GhostableInLibrary"` атрибут к записи в *Elements.xml*. Например,

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Разверните проект.

     Файлы копируются в указанные расположения в SharePoint.

## <a name="see-also"></a>См. также раздел
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
