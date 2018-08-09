---
title: 'Практическое: Добавление стандартных текстовых маркеров | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dd34b14b89c78d01f1d4acab57f33014860d7ba
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638825"
---
# <a name="how-to-add-standard-text-markers"></a>Практическое: Добавление стандартные текстовые метки
Используйте следующую процедуру для создания одного из типов маркеров текст по умолчанию, в состав [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базовым редактором.  
  
## <a name="to-create-a-text-marker"></a>Для создания текстового маркера  
  
1.  От того, используется ли в одной или двух трехмерной системе координат, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод для создания нового текстового маркера.  
  
     При таком вызове метода, укажите тип маркера, диапазон текста, чтобы создать маркер и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс. Затем этот метод возвращает указатель на только что созданный текстового маркера. Типы маркеров, взяты из <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> перечисления. Укажите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, если вы хотите быть в курсе событий маркера.  
  
    > [!NOTE]
    >  Создайте текстовые метки на только основной поток пользовательского интерфейса. Базовый редактор зависит от содержимого текстового буфера для создания меток текста и текстовый буфер не является потокобезопасным.  
  
## <a name="add-a-custom-command"></a>Добавление пользовательской команды  
 Реализация `IVsTextMarkerClient` интерфейс и передачи указателя на него из маркера улучшает поведение метки несколькими способами. Во-первых это позволяет обеспечить советы для метку и для выполнения команд. Это также позволяет получать уведомления о событиях для отдельных маркеров и для создания пользовательского контекстного меню через маркер. Используйте следующую процедуру для добавления пользовательской команды в контекстное меню маркера.  
  
### <a name="to-add-a-custom-command-to-the-context-menu"></a>Добавление пользовательской команды в контекстное меню  
  
1.  Перед отображением контекстного меню, среда вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> метода и передает проблема указатель на текстовый маркер и номер элемента команды в контекстном меню.  
  
     Примеры, характерные для точки останова команды в контекстном меню: **удалить точку останова** через **новую точку останова**, как показано на следующем снимке экрана.  
  
     ![Маркер контекстного меню](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Передайте некоторый текст, определяющее имя пользовательской команды. Например **удалить точку останова** может быть пользовательской команды, если среды не уже предоставил его. Можно также передать обратно ли команда поддерживается, доступна и включена, и/или переключить Вкл / Выкл. Среда использует эти сведения для отображения пользовательской команды в контекстном меню в правильный способ использования.  
  
3.  Чтобы выполнить команду, среда вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> метод, передав указатель для текстового маркера и количество команда, выбранная в контекстном меню.  
  
     Используйте эти сведения из этого вызова для выполнения, определяет вашей пользовательской команды нужные действия текстового маркера.  
  
## <a name="see-also"></a>См. также  
 [Использование меток текста с предыдущих версий API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Практическое: реализовать маркеры ошибок](../extensibility/how-to-implement-error-markers.md)   
 [Практическое: Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)   
 [Практическое: использовать текстовые метки](../extensibility/how-to-use-text-markers.md)