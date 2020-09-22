---
title: Руководство. Добавление стандартных текстовых маркеров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842369"
---
# <a name="how-to-add-standard-text-markers"></a>Практическое руководство. Добавление стандартных текстовых маркеров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Используйте следующую процедуру, чтобы создать один из типов текстовых маркеров по умолчанию, предоставляемых в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] основном редакторе.  
  
### <a name="to-create-a-text-marker"></a>Создание текстового маркера  
  
1. В зависимости от того, используете ли вы одну или двухмерную систему координат, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, чтобы создать новый текстовый маркер.  
  
     В этом вызове метода укажите тип маркера, диапазон текста для создания маркера, а также <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс. Затем этот метод возвращает указатель на только что созданный текстовый маркер. Типы маркеров берутся из <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> перечисления. Укажите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, если необходимо сообщить о событиях маркера.  
  
    > [!NOTE]
    > Создавать текстовые маркеры только в основном потоке пользовательского интерфейса. Основной редактор использует содержимое текстового буфера для создания текстовых маркеров, а текстовый буфер не является потокобезопасным.  
  
## <a name="adding-a-custom-command"></a>Добавление пользовательской команды  
 Реализация `IVsTextMarkerClient` интерфейса и указание указателя на него из маркера улучшает поведение маркера несколькими способами. Во первых, это позволяет предоставлять советы для маркера и выполнять команды. Это также позволяет получать уведомления о событиях для отдельных маркеров и создавать пользовательское контекстное меню над маркером. Используйте следующую процедуру, чтобы добавить пользовательскую команду в контекстное меню маркера.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Добавление пользовательской команды в контекстное меню  
  
1. Перед отображением контекстного меню среда вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> метод и передает вам указатель на затронутую текстовую метку и номер элемента команды в контекстном меню.  
  
     Например, команды, зависящие от точки останова в контекстном меню, включают в себя **Удаление точки останова** через **новую точку останова**, как показано на следующем снимке экрана.  
  
     ![Маркер контекстного меню](../extensibility/media/vsmarkercontextmenu.gif "всмаркерконтекстмену")  
  
2. Передайте некоторый текст, идентифицирующий имя пользовательской команды. Например, **Удаление точки останова** может быть пользовательской командой, если среда еще не предоставил ее. Вы также передаете значение, если команда поддерживается, доступна и включена, и/или выключена. Среда использует эти сведения для правильного вывода настраиваемой команды в контекстном меню.  
  
3. Для выполнения команды среда вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> метод, передавая вам указатель на текстовый маркер и номер команды, выбранной в контекстном меню.  
  
     Используйте эти сведения из этого вызова, чтобы выполнить любые действия текстового маркера, определяемого пользовательской командой.  
  
## <a name="see-also"></a>См. также:  
 [Использование текстовых маркеров с устаревшим API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Как реализовать маркеры ошибок](../extensibility/how-to-implement-error-markers.md)   
 [Как создавать пользовательские маркеры](../extensibility/how-to-create-custom-text-markers.md)   
 [Практическое руководство. Использование текстовых маркеров](../extensibility/how-to-use-text-markers.md)
