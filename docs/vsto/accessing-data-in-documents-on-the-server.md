---
title: Доступ к данным в документах на сервере
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ecfebda02096d1a36a5de84919aad65482a25ec0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="access-data-in-documents-on-the-server"></a>Доступ к данным в документах на сервере
  Вы можете программировать на данных в настройке уровня документа, без использования объектной модели Microsoft Office Word или Microsoft Office Excel. Это означает, что получить доступ к данным, содержащимся в документе на сервере, у которого нет Word или Excel. Например, код на сервере (например, в [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] страницы) можно настроить данных в документе и пересылать настроенный документ конечному пользователю. Когда конечный пользователь открывает документ, код привязки данных в сборке решения привязывает настроенные данные в документ. Это возможно, поскольку данные в документе, отделен от пользовательского интерфейса. Дополнительные сведения см. в разделе [кэшированных данных в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>Кэширование данных для использования на сервере  
 Чтобы кэшировать объект данных в документе, пометьте его с <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибута во время разработки, или используйте `StartCaching` метод ведущего элемента во время выполнения. При кэшировании объекта данных в документ, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] сериализует объект в XML-строку, хранящимся в документе. Объекты должны соответствовать определенным требованиям, чтобы соответствовать требованиям для кэширования. Дополнительные сведения см. в разделе [данные кэша](../vsto/caching-data.md).  

 Серверный код может обрабатывать любые объекты данных в кэше данных. Элементы управления, привязанные к экземплярам кэшированные данные синхронизируются с помощью пользовательского интерфейса, чтобы все серверные изменения, внесенные в данные отображаются автоматически при открытии документа на стороне клиента.  

## <a name="access-data-in-the-cache"></a>Доступ к данным в кэше  
 Данные в кэше доступны из приложения за пределами офиса, например из консольного приложения, приложения Windows Forms или веб-страницы. Приложение, которое обращается к кэшированным данным должна иметь полное доверие; веб-приложения с частичным доверием не может вставить, извлечь или изменить данные, кэшированные в документе Office.  

 Кэш данных доступен через иерархию коллекций, представляемых <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса:  

-   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Возвращает свойство <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, которое содержит все кэшированные данные в настройке на уровне документа.  

-   Каждый <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> содержит один или несколько <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> объектов. Объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> содержит все объекты кэшированных данных, которые определены в одном классе.  

-   Каждый <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> содержит один или несколько <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> объектов. Объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> представляет один объект кэшированных данных.  

 В следующем примере кода показано, как получить доступ к кэшированной строке в `Sheet1` класса в проекте книги Excel. Данный пример является частью большего примера, приведенного для <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> метод.  

 [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>Изменение данных в кэше  
 Чтобы изменить объект кэшированных данных, обычно выполните следующие действия:  

1.  Десериализует XML-представления кэшированного объекта в новый экземпляр объекта. Доступ к XML с помощью <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> свойство <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> , представляющий объект кэшированных данных.  

2.  Внесите изменения в эту копию.  

3.  Сериализация измененного объекта обратно в кэш данных, используя один из следующих вариантов:  

    -   Если вы хотите автоматически выполнить сериализацию объекта, используйте <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> метод. Этот метод использует **DiffGram** формат для сериализации <xref:System.Data.DataSet>, <xref:System.Data.DataTable>и объектов типизированного набора данных в кэше данных. **DiffGram** формат гарантирует, что изменения в кэше данных автономного документа передаются серверу правильно.  

    -   Если вы хотите выполнить собственную сериализацию для изменения кэшированных данных, можно написать непосредственно <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> свойство. Укажите **DiffGram** форматирования при использовании <xref:System.Data.Common.DataAdapter> обновление базы данных с помощью изменений, внесенных в данные в <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, или типизированного набора данных. В противном случае <xref:System.Data.Common.DataAdapter> обновит базу данных, добавляя новые строки вместо изменения существующих строк.  

### <a name="modify-data-without-deserializing-the-current-value"></a>Изменение данных без десериализации текущего значения  
 В некоторых случаях может потребоваться изменить значение кэшированного объекта без предварительной десериализации текущего значения. Например, это можно сделать при изменении значения объекта, имеющего простой тип, например, строку или целое число со знаком, или при инициализации кэшированной <xref:System.Data.DataSet> документа на сервере. В этих случаях можно использовать <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> метода без предварительной десериализации текущего значения кэшированного объекта.  

 В следующем примере кода показано, как изменение значения кэшированной строки в `Sheet1` класса в проекте книги Excel. Данный пример является частью большего примера, приведенного для <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> метод.  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>Изменение значений null в кэше данных  
 Кэш данных не хранит объекты, имеющие значение **null** при сохранении и закрытии документа. Это ограничение имеет несколько последствий при изменении кэшированных данных.  

-   Следует установить любого объекта в кэше данных значение **null**, все объекты в кэше данных автоматически присваивается значение **null** при открытии документа и все данные кэша будут очищены при сохранении и закрытии документа. То есть, все кэшированные объекты будут удалены из кэша данных и <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> коллекция будет пустой.  

-   При построении решения с **null** объектов в кэше данных, необходимо инициализировать данные объекты с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса перед документ открывается в первый раз, необходимо инициализировать все объекты в кэше данных. Если будут инициализированы только некоторые объекты, все объекты, будет присвоено **null** при открытии документа, и все данные кэша будут очищены при сохранении и закрытии документа.  

## <a name="access-typed-datasets-in-the-cache"></a>Доступ типизированных наборов данных в кэше  
 Если требуется доступ к данным в типизированный набор данных как из решения Office, так и из внешнего приложения Office, таких как приложения Windows Forms или [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] проекта, необходимо определить типизированный набор данных в отдельную сборку, упоминаются в проекты. При добавлении типизированный набор данных в каждом проекте с помощью **конфигурации источника данных** мастер или **конструктора наборов данных**, .NET Framework будет рассматривать типизированные наборы данных в двух проектах как имеющие разные типы . Дополнительные сведения о создании типизированных наборов данных см. в разделе [создания и настройки наборов данных в Visual Studio](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>См. также  
 [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md)  
