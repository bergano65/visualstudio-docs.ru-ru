---
title: Кэширование данных | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 094a4e6c639007fcf09ce28f0be2e398b8245858
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="caching-data"></a>Кэширование данных
  Можно кэшировать объекты данных в настройке на уровне документа, чтобы данные были доступны автономно или без открытия Microsoft Office Word или Microsoft Office Excel. Для кэширования объекта, объект должен иметь тип данных, отвечающий определенным требованиям. Многих распространенных типов данных в платформе .NET Framework этих требований, включая <xref:System.String>, <xref:System.Data.DataSet>, и <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Чтобы добавить объект в кэше данных двумя способами.  
  
-   Чтобы добавить объект в кэше данных при построении решения, примените <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибут объявления объекта. Дополнительные сведения см. в разделе [как: кэширование данных для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Чтобы программно добавить объект в кэше данных во время выполнения, используйте `StartCaching` метода ведущего элемента, такого как `ThisDocument` или `ThisWorkbook` классы. Дополнительные сведения см. в разделе [как: программное кэширование источника данных в документ Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 После добавления объекта в кэш данных, можно получить доступ к и изменять кэшированные, не запуская Word или Excel. Для получения дополнительной информации см. [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Требования для кэшируемых объектов данных  
 Чтобы кэшировать объект данных в решении, объект должен соответствовать следующим требованиям:  
  
-   Быть чтение и запись открытое поле или свойство ведущего элемента, например `ThisDocument` или `ThisWorkbook` классы.  
  
-   Не быть индексатором или другим параметризированным свойством.  
  
 Кроме того, объект данных должен быть сериализуем методом <xref:System.Xml.Serialization.XmlSerializer> класса, это означает тип объекта должен иметь следующие характеристики:  
  
-   Быть общедоступным.  
  
-   Иметь открытый конструктор без параметров.  
  
-   Не выполнять код, требующий дополнительных привилегий безопасности.  
  
-   Предоставляют только чтение и запись открытые свойства (другие свойства будут игнорироваться).  
  
-   Предоставляет многомерные массивы (вложенные массивы допускаются).  
  
-   Не возвращать интерфейсы из свойств и полей.  
  
-   Реализует <xref:System.Collections.IDictionary> если коллекция.  
  
 При кэшировании объекта данных [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] сериализует объект в XML-строку, которая хранится в *пользовательской XML-части* в документе. Для получения дополнительной информации см. [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Ограничения на размер кэшированных данных  
 Существуют некоторые ограничения на общий объем данных, которые можно добавить в кэш данных в документе и размера каждого отдельного объекта в кэше данных. При превышении этих ограничений, приложение может неожиданно при сохранении данных в кэше данных.  
  
 Чтобы избежать этих ограничений, необходимо выполните следующее:  
  
-   Не добавляйте в кэш данных любого объекта, размер которых превышает 10 МБ.  
  
-   Не добавляйте более 100 МБ данных в кэш данных в одном документе.  
  
 Это приблизительные значения. Точные ограничения зависят от нескольких факторов, включая доступный объем ОЗУ и количество выполняемых процессов.  
  
## <a name="controlling-the-behavior-of-cached-objects"></a>Управление поведением кэшированных объектов  
 Для большего контроля над поведением кэшированного объекта, можно реализовать <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> интерфейсом в типе кэшированного объекта. Например если вы хотите управлять, как пользователь получает уведомление при изменении объекта можно реализовать этот интерфейс. Примеры кода, демонстрирующие способы реализации <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, в разделе `ControlCollection` класс в пример динамических элементов управления Excel и Word пример динамических элементов управления в [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persisting-changes-to-cached-data-in-password-protected-documents"></a>Сохранение изменений к кэшированным данным в документах, защищенные паролем  
 Если кэшировать объекты данных в документе, защищенном паролем, изменения кэшированных данных не сохраняются. Можно сохранить изменения в кэшированных данных путем переопределения двух методов. Переопределить эти методы для временного удаления защиты при сохранении документа и повторно применить защиту после сохранения операция будет завершена.  
  
 Дополнительные сведения см. в разделе [как: данные кэша в защищенном документе](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="preventing-data-loss-when-adding-null-values-to-the-data-cache"></a>Предотвращение потери данных при добавлении нулевых значений в кэше данных  
 При добавлении объектов в кэш данных все кэшированные объекты должны быть инициализированы не-**null** значение перед сохранении и закрытии документа. Если любой кэшированный объект имеет **null** значение при сохранении и закрытии документа [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически удалит все кэшированные объекты из кэша данных.  
  
 Если добавить объект с **null** значение для кэширования данных с помощью <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибута во время разработки, можно использовать <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса для инициализации кэшированных данных объекты перед открытием документа. Это полезно, если необходимо инициализировать кэшированные данные на сервере без установленного перед конечным пользователем открыт документ Word или Excel. Для получения дополнительной информации см. [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>См. также  
 [Как: кэширование данных для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Как: программное кэширование источника данных в документах Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Как: кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Пошаговое руководство. Создание иерархического отношения с помощью кэшированного набора данных](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  