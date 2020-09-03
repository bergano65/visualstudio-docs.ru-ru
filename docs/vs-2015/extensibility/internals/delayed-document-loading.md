---
title: Отложенная загрузка документов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196860"
---
# <a name="delayed-document-loading"></a>Отложенная загрузка документов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Когда пользователь повторно открывает решение Visual Studio, большинство связанных документов не загружается немедленно. Фрейм окна документа создается в состоянии ожидания инициализации, а документ-заполнитель (называемый фреймом-заглушкой) помещается в таблицу выполняемых документов (РДТ).  
  
 Расширение может привести к тому, что документы проекта будут загружаться без необходимости путем запроса элементов в документах перед их загрузкой. Это может увеличить общий объем памяти для Visual Studio.  
  
## <a name="document-loading"></a>Загрузка документов  
 Фрейм заглушки и документ полностью инициализируются, когда пользователь обращается к документу, например, путем выбора вкладки рамки окна. Документ также может инициализироваться расширением, которое запрашивает данные документа, путем прямого доступа к РДТ для получения данных документа или доступа к РДТ косвенным образом, выполнив один из следующих вызовов:  
  
- Метод отображения фрейма окна: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- Метод Window Frame свойства <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> для любого из следующих свойств:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Если расширение использует управляемый код, не следует вызывать метод, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> Если нет уверенности, что документ не находится в состоянии ожидания инициализации, или вы хотите, чтобы документ был полностью инициализирован. Это происходит потому, что этот метод всегда возвращает объект данных doc, создавая его при необходимости. Вместо этого следует вызывать один из методов интерфейса IVsRunningDocumentTable4.  
  
  Если расширение использует C++, можно передать `null` ненужные параметры.  
  
  Вы можете избежать ненужной загрузки документа, вызвав один из следующих методов, прежде чем запрашивать соответствующие свойства: перед тем, как запрашивать другие свойства.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Этот метод возвращает <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> объект, который содержит значение, <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Если документ еще не инициализирован.  
  
  Узнать, когда документ был загружен, можно с помощью подписки на событие РДТ, которое возникает при полной инициализации документа. Существует две возможности:  
  
- Если приемник событий реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , можно подписываться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,  
  
- В противном случае можно подписываться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  Ниже приведен гипотетический сценарий доступа к документам. В расширении Visual Studio необходимо отобразить некоторые сведения об открытых документах, например число блокировок редактирования и что-то о данных документа. Он перечисляет документы в РДТ с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> , затем вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> для каждого документа, чтобы получить сведения об изменении количества блокировок и данных документа. Если документ находится в состоянии ожидания инициализации, запрос данных документа приводит к необязательной инициализации.  
  
  Более эффективный способ — использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> для получения счетчика блокировок редактирования, а затем использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> для определения того, был ли документ инициализирован. Если флаги не включены <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , документ уже инициализирован, и запрос данных документа с помощью не <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> приводит к ненужной инициализации. Если флаги включены <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , расширение должно избегать запроса данных документа до инициализации документа. Это можно обнаружить в обработчике событий Онафтераттрибутечанже (ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Тестирование расширений для проверки принудительной инициализации  
 Отсутствует видимая подсказка, указывающая, был ли документ инициализирован, поэтому может быть трудно выяснить, что расширение является принудительной инициализацией. Можно задать раздел реестра, который упрощает проверку, так как в этом случае заголовок каждого документа, который не был полностью инициализирован, будет содержать текст `[Stub]` в заголовке.  
  
 В **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]** задайте для **стубтабтитлеформатстринг** значение ** {0} [заглушка]**.
