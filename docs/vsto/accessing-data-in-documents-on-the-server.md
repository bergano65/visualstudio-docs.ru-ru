---
title: Доступ к данным в документах на сервере
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d815178e772e391eb19eb43b5870fbcd9dbdaa6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858108"
---
# <a name="access-data-in-documents-on-the-server"></a>Доступ к данным в документах на сервере
  Данные в настройке уровня документа можно программировать без использования объектной модели Microsoft Office Word или Microsoft Office Excel. Это означает, что вы сможете использовать данные, содержащиеся в документе на сервере, где установлен Microsoft Word или Excel. Например, код на сервере (например, в [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] страницы) можно настроить данные в документе и пересылать настроенный документ для конечного пользователя. Когда конечный пользователь открывает документ, код привязки данных в сборке решения привязывает настроенные данные в документ. Это возможно, так как данные в документе, отделен от пользовательского интерфейса. Дополнительные сведения см. в разделе [кэшированных данных в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Кэширование данных для использования на сервере
 Чтобы кэшировать объект данных в документе, пометьте его с <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибут во время разработки, или используйте `StartCaching` метод ведущего элемента во время выполнения. При кэшировании объекта данных в документе, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] сериализует объект в строку XML, которые хранятся в документе. Объекты должны соответствовать определенным требованиям, чтобы быть пригодны для кэширования. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).

 Серверный код может обрабатывать любые объекты данных в кэше данных. Элементы управления, привязанные к экземплярам кэшированные данные синхронизируются с пользовательским интерфейсом, таким образом, любые изменения на стороне сервера, данные будут отображаться автоматически при открытии документа на стороне клиента.

## <a name="access-data-in-the-cache"></a>Доступ к данным в кэше
 Данные в кэше доступны из приложения за пределами офиса, например из консольного приложения, в приложении Windows Forms или веб-страницы. В приложении, которое обращается к кэшированным данным должна быть полным доверием; веб-приложения с частичным доверием не может вставить, извлечь или изменить данные, кэшированные в документах Office.

 Кэш данных доступен через иерархию коллекций, предоставляемых <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса:

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Возвращает <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, которое содержит все кэшированные данные в настройке уровня документа.

- Каждый <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> содержит один или несколько <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> объектов. Объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> содержит все объекты кэшированных данных, которые определены в одном классе.

- Каждый <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> содержит один или несколько <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> объектов. Объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> представляет один объект кэшированных данных.

  В следующем примере кода показано, как получить доступ к кэшированной строке в `Sheet1` класс проекта книги Excel. Этот пример является частью большего примера, предоставляемый для <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> метод.

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Изменение данных в кэше
 Чтобы изменить объект кэшированных данных, обычно выполните следующие действия:

1.  Десериализует XML-представление кэшированного объекта в новый экземпляр объекта. Доступ к XML с помощью <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> свойство <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> , представляющий кэшированного объекта данных.

2.  Внесите изменения в эту копию.

3.  Выполнить сериализацию измененного объекта обратно в кэш данных с помощью одного из следующих вариантов:

    -   Если вы хотите автоматически выполнить сериализацию объекта, используйте <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> метод. Этот метод использует **DiffGram** формат для сериализации <xref:System.Data.DataSet>, <xref:System.Data.DataTable>и объектов типизированного набора данных в кэше данных. **DiffGram** формат гарантирует, что изменения в кэше данных автономного документа отправляются на сервер, правильно.

    -   Если вы хотите выполнить собственную сериализацию изменений к кэшированным данным, можно написать непосредственно к <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> свойство. Укажите **DiffGram** форматирования при использовании <xref:System.Data.Common.DataAdapter> обновление базы данных с изменениями, произведенных над данными в <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, или типизированного набора данных. В противном случае <xref:System.Data.Common.DataAdapter> обновит базу данных путем добавления новых строк вместо изменения существующих строк.

### <a name="modify-data-without-deserializing-the-current-value"></a>Изменение данных без десериализации текущего значения
 В некоторых случаях может потребоваться изменить значение кэшированного объекта без предварительной десериализации текущего значения. Например, это можно сделать при изменении значения объекта, который имеет простой тип, например строку или целое число, или при инициализации кэшированный <xref:System.Data.DataSet> документа на сервере. В таких случаях можно использовать <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> метода без предварительной десериализации текущего значения кэшированного объекта.

 В следующем примере кода показано, как изменить значение кэшированной строке в `Sheet1` класс проекта книги Excel. Этот пример является частью большего примера, предоставляемый для <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> метод.

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Изменение значения null в кэше данных
 Кэш данных не хранит объекты, имеющие значение **null** при сохранении и закрытии документа. Это ограничение имеет несколько последствий при изменении кэшированных данных.

-   Следует установить любой объект в кэше данных к значению **null**, все объекты в кэше данных будет автоматически присвоено **null** при открытии документа, и будет очистить кэш данных, когда Сохранить и закрыть документ. То есть, все кэшированные объекты будут удалены из кэша данных и <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> коллекция будет пустой.

-   При построении решения на основе **null** объектов в кэше данных и вы хотите инициализировать эти объекты с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса перед документ открывается в первый раз, необходимо инициализировать все объекты в кэше данных. Если инициализируется только часть объектов, все объекты, будет присвоено **null** при открытии документа, и будет очистить кэш данных, при сохранении и закрытии документа.

## <a name="access-typed-datasets-in-the-cache"></a>Доступ типизированных наборов данных в кэше
 Если требуется доступ к данным в типизированном наборе данных как из решения Office, так и из приложения за пределами офиса, например приложение Windows Forms или [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] проекта, необходимо определить типизированный набор данных в отдельную сборку, которая упоминается в обоих проекты. При добавлении типизированный набор данных в каждом проекте с помощью **конфигурации источника данных** мастер или **конструктор наборов данных**, .NET Framework будет рассматривать типизированные наборы данных в двух проектах как разные типы . Дополнительные сведения о создании типизированных наборов данных см. в разделе [Создание и Настройка наборов данных в Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>См. также

- [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)
- [Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md)