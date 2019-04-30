---
title: Встроенная активация | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 192274d087731f68cb7e01c1da20e80cbfef0360
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446415"
---
# <a name="in-place-activation"></a>Активация на месте
Если в представлении редактора размещаются элементы ActiveX или другие активные элементы управления, представление редактора следует реализовать как элемент ActiveX или как активный объект данных документа с помощью модели встроенной активации.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Поддержка меню, панелей инструментов и команд  
 Visual Studio допускает использование в представлении редактора меню и панелей инструментов интегрированной среды разработки. Такие расширения называются *встроенными компонентами OLE*. Дополнительные сведения см. в разделах <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> и <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 При реализации элемента ActiveX можно размещать другие внедренные объекты. При реализации объекта данных документа рамка окна ограничивает возможность использования элементов ActiveX.  
  
> [!NOTE]
> Интерфейсы <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> обеспечивают разделение данных и представления. Однако в Visual Studio такая возможность не поддерживается, и эти интерфейсы используются только для представления объекта представления документа.  
  
 Редакторы, использующие службу <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> , могут обеспечивать интеграцию с меню, панелями инструментов и командами путем вызова методов интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> , реализуемого службой <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Редакторы также могут предоставлять и другие функциональные возможности Visual Studio, такие как отслеживание выделения и управление отменой действий. Дополнительные сведения см. в разделе [создания пользовательских редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Используемые объекты и интерфейсы  
 Объекты, используемые для реализации встроенной активации, показаны на рисунке ниже.  
  
 ![В&#45;поместите редактор активации](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Редактор встроенной активации  
  
> [!NOTE]
> Из объектов, показанных на этой схеме, только объект `CYourEditorFactory` требуется для создания стандартного редактора. Если вы создаете настраиваемый редактор, реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> не нужно, так как ваш редактор, скорее всего, будет иметь собственный закрытый механизм сохраняемости. Дополнительные сведения см. в разделе [создания пользовательских редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md).  
  
 Все интерфейсы, реализуемые для создания редактора встроенной активации, показаны в одном объекте `CYourEditorDocument` , но такая конфигурация поддерживает только одно представление данных документа. Дополнительные сведения о поддержке нескольких представлений данных документа см. в разделе [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
|Интерфейс|Тип объекта|Использовать|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Просмотр|Позволяет встроенным объектам VSPackage работать как полностью интегрированным компонентам интегрированной среды разработки с помощью службы <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Эта служба интегрирует меню, панели инструментов и команды объекта в интегрированную среду разработки и отправляет уведомления об изменениях состояния.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Просмотр|Основное средство, с помощью которого внедренный объект предоставляет основные функциональные возможности своему контейнеру и взаимодействует с ним.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Просмотр|Управляет активацией и деактивацией встроенных объектов и определяет, какая часть встроенного объекта должна быть видимой.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Просмотр|Предоставляет прямой канал связи между встроенным объектом, внешней рамкой окна связанного приложения и окном документа в приложении, которое содержит внедренный объект.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Просмотр|Реализует объект ActiveX. Обратите внимание, что методы <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> и `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` , которые разделяют данные документа и представление, не используются в интегрированной среде разработки.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Представление и данные|Позволяет объекту данных документа, объекту представления документа или им обоим принимать участие в обработке команд.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Просмотр|Обеспечивает обновление строки состояния.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Просмотр|Обеспечивает добавление элементов на панель элементов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Данные|Отправляет уведомления об изменениях в редактируемом файле. (Этот интерфейс является необязательным.)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Данные|Используется для включения функции "Сохранить как" для типа файлов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Данные|Обеспечивает сохраняемость документа. Чтобы файлы, доступные только для чтения, обозначались значком с изображением замка, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Данные|Определяет, следует ли игнорировать изменения в данных документа.|