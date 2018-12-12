---
title: Кэшированные данные в настройках уровня документа
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c17c24dda11ea210c190a31197b783036357f2de
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248300"
---
# <a name="cached-data-in-document-level-customizations"></a>Кэшированные данные в настройках уровня документа
  Основная цель настроек уровня документа является отделение данных из представления в документах Office. Данные относятся к информации, хранящейся в документе, включая числовые и текстовые значения. Представление ссылается на пользовательский интерфейс и объектной модели Microsoft Office Word и Microsoft Office Excel.  
  
 Visual Studio отделяет данные от представления в настройках уровня документа, позволяя включить данные в качестве *острова данных*, называемой *кэш данных*. Можно считывать или изменять данные напрямую, без запуска Word или Excel. Это полезно в тех случаях, когда необходимо изменять данные в документах на сервере, который не установлен Microsoft Office. Word и Excel предназначены для использования в клиентских средах; они не предназначены для запуска на сервере.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Дополнительные сведения о настройках уровня документа, см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) и [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Сведения о модели программирования кэшированных данных  
 Острова данных может содержать любой объект в решении, которое соответствует определенным требованиям. Эти объекты включают в себя <xref:System.Data.DataSet> объектов, <xref:System.Data.DataTable> объектов и любой другой объект, который может быть сериализован с <xref:System.Xml.Serialization.XmlSerializer> класса. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).  
  
 Для представления кэшированных данных, можно привязать элементы управления Windows Forms и *элементы управления ведущего приложения* документ, чтобы объекты в области данных. Привязка данных между областью данных и элементов управления с привязкой данных способствует их синхронизации. Можно также добавить код проверки к данным, который не зависит от элементов управления. Дополнительные сведения см. в разделе [привязки данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Элементы управления ведущего приложения являются расширенными версиями собственные объекты в объектных моделях Word и Excel. В отличие от собственных объектов элементы управления ведущего приложения может быть привязаны непосредственно к объектам управляемых данных. Дополнительные сведения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md) и [элементы управления Windows Forms на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Доступа к кэшированным данным на сервере  
 Для доступа к кэшированным данным в документе, можно использовать <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса. Этот класс является частью [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], и он может использоваться на сервере без запуска приложений Excel или Word. Когда пользователь открывает документ, после внесения изменений в кэшированных данных, любые элементы управления, привязанных к данным, автоматически синхронизируются с изменения и пользователь получает обновленные данные. Дополнительные сведения см. в разделе [доступа к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel и Word для записи данных на сервере, только для того, чтобы просмотреть его на стороне клиента не требуются. Excel и Word даже не нужно установить на сервере. Это обеспечивает лучшую масштабируемость и возможность выполнения быстрой пакетной обработки документов, содержащих области данных.  
  
## <a name="data-caching-for-offline-use"></a>Кэширование данных для автономного использования  
 Хранение данных в область данных позволяет сценарии автономной работы. Когда пользователь сначала открывает документ или запрашивает документ с сервера, остров данных заполняется самыми последними данными. Острова данных кэшируется в документе, а затем будет доступно вне сети. Пользователь (и код) можно управлять данными, даже если интерактивное подключение не будет доступна. При повторном подключении пользователя, изменения в данные могут передаваться обратно в источник данных на сервере.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Кэшированных данных и пользовательских XML-частей по сравнению с  
 Настраиваемые XML-части появились в Microsoft Office system 2007 как способ хранения произвольных фрагментов XML в документе. Несмотря на то, что пользовательские XML-части бывают полезны в тех же сценариях кэша данных, существуют некоторые различия между областью данных и пользовательских XML-частей. Дополнительные сведения о пользовательских XML-частях см. в разделе [Общие сведения о пользовательских XML частях](../vsto/custom-xml-parts-overview.md).  
  
 В следующей таблице перечислены некоторые различия и сходства.  
  
||Кэш данных|Настраиваемые XML-части|  
|-|----------------|----------------------|  
|Какие приложения Office могут использовать их?|Настройки уровня документа для следующих приложений:<br /><br /> -Excel<br />-Word|Решения уровня документа и уровня приложения для следующих приложений:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|Типы данных можно хранить?|Открытый объект в сборке настройки, отвечающий определенным требованиям. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).|Любые данные XML.|  
|Доступны ли данные без запуска приложения Microsoft Office?|Да, с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс, предоставляемый [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Да, с помощью классов в <xref:System.IO.Packaging> пространства имен, или с помощью пакета SDK формата Open XML.|  
  
## <a name="see-also"></a>См. также  
 [Данные в решениях Office](../vsto/data-in-office-solutions.md)   
 [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  