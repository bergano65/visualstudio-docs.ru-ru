---
title: "Кэшированные данные в настройках уровня документа | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1fe9465c3f238941ace0d5b6fc438c7d5d93ec64
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="cached-data-in-document-level-customizations"></a>Кэшированные данные в настройках уровня документа
  Основная цель настроек уровня документа — отделение данных от представления в документах Office. Данные относятся к сведениям, хранящимся в документе, включая числа и текст. Представление ссылается на пользовательский интерфейс и объектной модели Microsoft Office Word и Microsoft Office Excel.  
  
 Visual Studio отделяет данные от представления в настройках уровня документа, позволяя включить данные в качестве *острова данных*, который также называется *кэш данных*. Может считывать или изменять данные напрямую, не запуская Word или Excel. Это полезно, если нужно будет изменять данные в документах на сервере, который не установлен Microsoft Office. Word и Excel, предназначены для использования в клиентских средах; они не предназначены для выполнения на сервере.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Дополнительные сведения о настройках уровня документа см. в разделе [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) и [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understanding-the-cached-data-programming-model"></a>Основные сведения о модели программирования кэшированных данных  
 Область данных может содержать любой объект в решении, отвечающий определенным требованиям. Эти объекты включают <xref:System.Data.DataSet> объектов, <xref:System.Data.DataTable> объектов и любой другой объект, могут быть сериализованы с <xref:System.Xml.Serialization.XmlSerializer> класса. Дополнительные сведения см. в разделе [кэширование данных](../vsto/caching-data.md).  
  
 Для представления кэшированных данных можно привязать элементы управления Windows Forms и *элементы управления ведущего приложения* документ, чтобы объекты в области данных. Привязка данных между областью данных и элементы управления с привязкой к данным способствует их синхронизации. Можно также добавить код проверки к данным, которая не зависит от элементов управления. Дополнительные сведения см. в разделе [привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Элементы управления ведущего приложения являются расширенными версиями собственные объекты в объектных моделях Word и Excel. В отличие от собственных объектов элементы управления ведущего приложения могут быть привязаны непосредственно к объектам управляемых данных. Дополнительные сведения см. в разделах [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) и [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="accessing-cached-data-on-the-server"></a>Доступ к кэшированным данным на сервере  
 Чтобы получить доступ к кэшированным данным в документе, можно использовать <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса. Этот класс является частью [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], и он может использоваться на сервере без запуска приложений Excel или Word. Когда пользователь открывает документ, после изменения кэшированных данных, все элементы управления, привязанные к данным, автоматически синхронизируются с изменениями и пользователю предоставляется с обновленными данными. Для получения дополнительной информации см. [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel и Word не требуется для записи данных на сервере только для просмотра на стороне клиента. Excel и Word даже не нужно установить на сервере. Это обеспечивает улучшенную масштабируемость и возможность выполнения быстрой пакетной обработки документов, содержащих области данных.  
  
## <a name="data-caching-for-offline-use"></a>Кэширование данных для автономного использования  
 Хранение данных в область данных включает автономные сценарии. При первом пользователь открывает документ или запрашивает документ с сервера, область данных заполняется самыми последними данными. Острова данных кэшируется в документе и затем становится доступным автономно. Пользователь (и код) можно управлять данными, даже если интерактивное подключение не будет. При повторном подключении пользователя, изменения в данные могут передаваться обратно в источник данных на сервере.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Кэшированные данные и сравнение пользовательских XML-частей  
 Настраиваемые XML-части появились в выпуске 2007 системы Microsoft Office, например для хранения произвольных фрагментов XML в документе. Несмотря на то, что пользовательские XML-части пригодны для многих сценариев, подобных кэш данных, существуют некоторые различия между областью данных и пользовательских XML-частей. Дополнительные сведения о пользовательских XML-частях см. в разделе [Общие сведения о пользовательских частей XML](../vsto/custom-xml-parts-overview.md).  
  
 В следующей таблице перечислены некоторые различия и сходства.  
  
||Кэш данных|Настраиваемые XML-части|  
|-|----------------|----------------------|  
|Какие приложения Office можно использовать?|Настройки уровня документа для следующих приложений:<br /><br /> -Excel<br />-Word|Решения уровня документа и уровня приложения для следующих приложений:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|Типы данных для хранения.|Открытый объект в сборке настройки, отвечающий определенным требованиям. Для получения дополнительной информации см. [Caching Data](../vsto/caching-data.md).|XML-данных.|  
|Доступны данные без запуска приложения Microsoft Office?|Да, с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс, предоставляемый [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Да, с помощью классов в <xref:System.IO.Packaging> пространства имен, или с помощью пакета SDK формата Open XML.|  
  
## <a name="see-also"></a>См. также  
 [Данные в решениях Office](../vsto/data-in-office-solutions.md)   
 [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  