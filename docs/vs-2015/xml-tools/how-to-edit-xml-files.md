---
title: 'Практическое: изменять XML-файлы | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac3864b3d3a3074f9b6be2529e8f674df90532c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245301"
---
# <a name="how-to-edit-xml-files"></a>Как изменять XML-файлы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Редактор XML - это новый редактор для XML-файлов. Его можно использовать для отдельных XML-файлов или файлов, связанных с проектами Visual Studio. Редактор XML связан со следующими расширениями файлов: CONFIG, DTD, XML, XSD, XDR, XSLT и VSSETTINGS. Для редактора XML также зарегистрированы файлы всех типов с содержимым в формате XML или DTD, для которых не зарегистрирован специальный редактор.  
  
> [!NOTE]
>  Документы XHTML обрабатываются редактором HTML.  
  
### <a name="to-edit-an-xml-file"></a>Редактирование XML-файла  
  
1.  Дважды щелкните файл, который нужно изменить.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>Добавление нового XML-файла в существующий проект  
  
1.  Из **проекта** меню, выберите **Добавление нового элемента**.  
  
2.  Выберите **XML-файл** из **шаблоны** области.  
  
3.  Введите имя файла в **имя** поле и нажмите клавишу **добавить**.  
  
     XML-файл добавляется в проект и открывается в редакторе XML. Этот файл содержит XML-декларацию по умолчанию, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>Добавление существующего XML-файла в проект  
  
1.  Из **проекта** меню, выберите **добавить существующий элемент**.  
  
     **Добавить существующий элемент** откроется диалоговое окно.  
  
2.  Выберите XML-файл и нажмите клавишу **добавить**.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>Создание нового XML-файла или XSLT-файла  
  
1.  Из **файл** меню, выберите **New**.  
  
     **Новый файл** откроется диалоговое окно.  
  
2.  Выберите **XML-файл** создать новый XML-файл; или выберите **XSLT-файл** для создания новой таблицы стилей XSLT.  
  
3.  Нажмите кнопку **откройте**.  
  
### <a name="to-create-a-project-for-xml-files"></a>Создание проекта для XML-файлов  
  
1.  Из **файл** меню, выберите **New**, а затем выберите **проекта**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
2.  Выберите язык кода по своему усмотрению, выберите **пустой проект**и нажмите кнопку **ОК**.  
  
3.  Добавьте XML-файлы в проект.  
  
     Редактор XML найдет добавленные в этот проект схемы и применит их для проверки правильности документа и поддержки технологии IntelliSense в любых XML-файлах, схемах или XSLT-файлах, редактируемых во время того, как открыт этот проект.  
  
## <a name="see-also"></a>См. также  
 [Редактор XML](../xml-tools/xml-editor.md)   
 [Свойства XML-документа, окно "Свойства"](../xml-tools/xml-document-properties-properties-window.md)   
 [Как создать XML-схему из XML-документа](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)



