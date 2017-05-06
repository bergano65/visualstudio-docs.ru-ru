---
title: "Доступ к данным в документах на сервере"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "данные [разработка решений Office в Visual Studio], доступ к серверу"
  - "доступ к данным [разработка решений Office в Visual Studio]"
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Доступ к данным в документах на сервере
  Можно программировать относительно данных в настройке на уровне документа без необходимости использования объектной модели Microsoft Office Word или Microsoft Office Excel.  Это означает, что можно получить доступ к данным, содержащимся в документе на сервере, на котором не установлены Word или Excel.  Например, код на сервере \(например, на странице [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\) может выполнять настройку данных в документе и пересылать настроенный документ конечному пользователю.  Когда конечный пользователь открывает документ, код привязки данных в сборке решения привязывает настроенные данные к документу.  Это возможно, поскольку данные в документе отделены от пользовательского интерфейса.  Дополнительные сведения см. в разделе [Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Кэширование данных для использования на сервере  
 Для кэширования объекта данных в документе следует пометить его во время разработки атрибутом <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>, либо использовать метод `StartCaching` ведущего элемента во время выполнения.  При кэшировании объекта данных в документ, среда [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] сериализует объект в XML\-строку, которая сохраняется в документе.  Чтобы объекты были пригодны для кэширования, они должны соответствовать определенным требованиям.  Дополнительные сведения см. в разделе [Кэширование данных](../vsto/caching-data.md).  
  
 Код на стороне сервера может обрабатывать любые объекты данных в кэше данных.  Элементы управления, связанные с экземплярами кэшированных данных, синхронизированы с пользовательским интерфейсом, так что любые изменения данных на стороне сервера автоматически отображаются, когда документ открывается на клиентской стороне.  
  
## Доступ к данным в кэше  
 Доступ к данным в кэше может выполняться из приложений вне Office, например из консольного приложения, из приложения Windows Forms или из веб\-страницы.  Приложение, которое обращается к кэшированным данным, должно иметь полное доверие; веб\-приложение с частичным доверием не может вставлять, извлекать или изменять данные, кэшированные в документе Office.  
  
 К кэшу данных имеется доступ через иерархию коллекций, представленных свойством <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> класса <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  
  
-   Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> возвращает объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, содержащий кэшированные данные в настройке на уровне документа.  
  
-   Каждый объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> содержит один или несколько объектов <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>.  Объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> содержит все объекты кэшированных данных, определенные в одном классе.  
  
-   Каждый объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> содержит один или несколько объектов <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>.  Объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> представляет один объект кэшированных данных.  
  
 Следующий пример кода демонстрирует доступ к кэшированной строке в классе `Sheet1` проекта рабочей книги Excel.  Этот пример кода является частью более масштабного примера для метода<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>.  
  
 [!code-csharp[Trin_ServerDocument#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#12)]  
  
## Изменение данных в кэше  
 Чтобы изменить объект кэшированных данных, необходимо выполнить следующие действия:  
  
1.  Выполнить десериализацию XML\-представления кэшированного объекта в новый экземпляр объекта.  Доступ к XML можно получить с помощью свойства <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> элемента <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>, представляющего объект кэшированных данных.  
  
2.  Внесите изменения в данную копию.  
  
3.  Выполните сериализацию измененного объекта обратно в кэш данных, используя одну из следующих функций:  
  
    -   Если необходимо выполнить автоматическую сериализацию изменений, следует использовать метод <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>.  Этот метод использует формат **DiffGram** для сериализации <xref:System.Data.DataSet>, <xref:System.Data.DataTable> и объектов типизированного набора данных в кэше данных.  Формат **DiffGram** гарантирует, что изменения в кэше данных автономного документа передаются серверу правильно.  
  
    -   Если необходимо выполнить собственную сериализацию изменений в кэшированные данные, можно написать код непосредственно в свойстве <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>.  Задайте формат **DiffGram**, если <xref:System.Data.Common.DataAdapter> используется для обновления базы данных изменениями, выполненными в данных в <xref:System.Data.DataSet>, <xref:System.Data.DataTable> или в типизированном наборе данных.  В противном случае <xref:System.Data.Common.DataAdapter> будет обновлять базу данных, добавляя новые строки вместо изменения существующих строк.  
  
### Изменение данных без сериализации текущего значения  
 В отдельных случаях необходимо изменить значение кэшированного объекта без предварительной десериализации текущего значения.  Например, это может понадобиться в случае изменения значения объекта, имеющего простой тип, к примеру, строки или целого числа; либо в случае инициализации кэшированного объекта <xref:System.Data.DataSet> в документе на сервере.  В таком случае можно использовать метод <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> без предварительной десериализации текущего значения кэшированного объекта.  
  
 Следующий пример кода демонстрирует изменение значения кэшированной строки в классе `Sheet1` проекта рабочей книги Excel.  Этот пример кода является частью более масштабного примера для метода<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>.  
  
 [!code-csharp[Trin_ServerDocument#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#11)]  
  
### Изменение нулевого значения в кэше данных  
 Кэш данных не хранит объекты, имеющие значение **null**, при сохранении или закрытии документа.  Вследствие данного ограничения при изменении кэшированных данных происходит следующее:  
  
-   Если какому\-либо объекту в кэше данных присвоено значение **null**, всем объектам в кэше данных автоматически присваивается значение **null** при открытии документа; при сохранении и закрытии документа будет выполнена полная очистка кэша данных.  То есть, все кэшированные объекты будут удалены из кэша данных и коллекция <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> будет пуста.  
  
-   При построении решения с объектами **null** в кэше данных, если необходимо инициализировать данные объекты с помощью класса <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> до первого открытия документа, следует проверить, чтобы все объекты в кэше данных были инициализированы.  Если будут инициализированы только некоторые объекты, всем объектам при открытии документа будет присвоено значение **null**, и при сохранении и закрытии документа будет выполнена полная очистка кэша данных.  
  
## Доступ к типизированным наборам данных в кэше  
 Если необходимо обращаться к данным в типизированном наборе данных как из решения Office, так и из приложения, не входящего в пакет Office, например приложения Windows Forms или проекта [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], необходимо определить типизированный набор данных в отдельной сборке, на которую будут ссылаться оба проекта.  Если типизированный набор данных добавляется к каждому проекту при помощи **мастера настройки источника данных** или **конструктора наборов данных**, .NET Framework будет рассматривать типизированные наборы данных в двух проектах как имеющие разные типы.  Сведения о создании типизированных наборов данных см. в разделе [Практическое руководство. Создание типизированного набора данных](../Topic/Creating%20and%20configuring%20datasets%20in%20Visual%20Studio.md).  
  
## См. также  
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md)  
  
  