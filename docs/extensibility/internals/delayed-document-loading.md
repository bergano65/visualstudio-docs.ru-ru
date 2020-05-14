---
title: Задержка загрузки документов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708811"
---
# <a name="delayed-document-loading"></a>Задержка загрузки документов

Когда пользователь вновь открывает решение Visual Studio, большинство связанных с ними документов загружаются не сразу. Оконная рама документа создается в состоянии неинициализации, а документ заполнителя (так называемый кадр заглушки) помещается в таблицу «Бегущий документ» (RDT).

Ваше расширение может привести к ненужной загрузке проектных документов путем запроса элементов в документах перед их загрузкой, что может увеличить общий объем памяти Visual Studio.

## <a name="document-loading"></a>Загрузка документов

Рамка заглушки и документ полностью инициализированы, когда пользователь получает доступ к документу, например, выбрав вкладку оконной рамы. Документ также может быть инициализирован путем расширения, которое запрашивает данные документа, либо путем доступа к RDT непосредственно для получения данных документа, или доступа к RDT косвенно, сделав один из следующих вызовов:

- Метод оконной рамы. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>

- Метод оконной рамы <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> на любом из следующих свойств:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Если расширение использует управляемый код, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> вы не должны звонить, если вы не уверены, что документ не находится в состоянии неинициализации, или вы хотите, чтобы документ был полностью инициализирован. Причина в том, что метод всегда возвращает объект данных документа, создавая его при необходимости. Вместо этого следует вызвать один из `IVsRunningDocumentTable4` методов на интерфейсе.

- Если в вашем расширении используется `null` СЗ, вы можете пройти по параметрам, которые вы не хотите.

- Вы можете избежать ненужной загрузки документов, позвонив в один из следующих методов, прежде чем попросить соответствующие свойства, прежде чем попросить другие свойства:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>с помощью [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Этот метод <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> возвращает объект, который включает значение для [_VSRDTFLAGS4. RDT_PendingInitialization,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) если документ еще не был инициализирован.

Вы можете узнать, когда документ был загружен, подписавшись на событие RDT, которое поднимается, когда документ полностью инициализирован. Есть две возможности:

- Если событие раковина <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>реализует, вы <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>можете подписаться на,

- В противном случае, вы можете подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.

Следующим примером является гипотетический сценарий доступа к документу: расширение Visual Studio хочет отображать некоторую информацию об открытых документах, например количество блокировки и что-то о данных документа. Он перечисляет документы в RDT <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>с <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> помощью, а затем требует для каждого документа для того, чтобы получить количество блокировки отсечения и документ данных. Если документ находится в состоянии неинициализации, запрос данных документа приводит к тому, что он излишне инициализирован.

Более эффективным способом доступа к документу является использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> для подсчета <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> блокировки, а затем для определения того, был ли документ инициализирован. Если флаги не включают [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)документ уже инициализирован, и запрос <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> данных документа не вызывает никакой ненужной инициализации. Если флаги включают [_VSRDTFLAGS4. RDT_PendingInitialization,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)расширение должно избегать запроса данных документа до тех пор, пока документ не будет инициализирован. Эта инициализация может `OnAfterAttributeChange(Ex)` быть обнаружена в обработчике событий.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Продление тестирования, чтобы увидеть, принудят ли они инициализацию

Нет видимого сигнала, чтобы указать, был ли документ инициализирован, поэтому может быть трудно выяснить, является ли ваше расширение форсированием инициализации. Вы можете установить ключ реестра, который упрощает проверку, поскольку он вызывает название каждого документа, который не полностью инициализирован, чтобы иметь текст *«Stub»* в заголовке.

В **HKEY_CURRENT_USER»Программное обеспечение»Microsoft-VisualStudio »14.0 »BackgroundSolutionLoad**, установите **StubTabTitleFormatString** на * {0} «Stub».*
