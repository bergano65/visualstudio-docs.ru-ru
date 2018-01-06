---
title: "Как: Добавление маркеров стандартный текст | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bdcdbabae26a9116b1e00910ecef2f83f4075551
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-standard-text-markers"></a>Как: Добавление маркеров стандартного текста
Используйте следующую процедуру для создания одного из типов маркеров текст по умолчанию, в состав [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора.  
  
### <a name="to-create-a-text-marker"></a>Для создания маркера текста  
  
1.  В зависимости от того, используется ли один или два - измерений системы координат, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метода или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод для создания нового текстовой метки.  
  
     При вызове этого метода, укажите тип маркера, диапазон текста для создания маркера по и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейса. Затем этот метод возвращает указатель на только что созданный текстовая метка. Типы маркеров, взяты из <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> перечисления. Укажите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, чтобы быть в курсе событий маркера.  
  
    > [!NOTE]
    >  Создание текстовых меток в основном потоке пользовательского интерфейса только. Базовый редактор зависит от содержимое текстового буфера для создания текстовых маркеров: и текстовый буфер не является потокобезопасным.  
  
## <a name="adding-a-custom-command"></a>Добавление пользовательской команды  
 Реализация `IVsTextMarkerClient` интерфейс и предоставление указатель из маркера расширяет поведение маркера несколькими способами. Во-первых это позволяет в целях обеспечения советы метку и для выполнения команд. Это также позволяет получать уведомления о событиях для отдельных маркеров и для создания пользовательского контекстного меню над маркера. Используйте следующую процедуру для добавления пользовательской команды в контекстное меню маркера.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Добавление пользовательской команды в контекстное меню  
  
1.  Вызывается перед отображением контекстного меню среды <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> метод и передает проблема указатель на текст маркера и количества элемента команды в контекстном меню.  
  
     Примеры: характерные для точки останова команды в контекстном меню **удалить точку останова** через **новую точку останова**, как показано на следующем снимке экрана.  
  
     ![Маркер контекстного меню](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Передайте часть текста, идентифицирующее имя пользовательской команды. Например **удалить точку останова** может быть пользовательской команды, если среда не уже предоставил его. Можно также передать обратно ли команда поддерживается, доступна и включена, и/или включения или выключения переключателя. В среде эти сведения используется для отображения пользовательской команды в контекстном меню в правильный способ.  
  
3.  Для выполнения команды, среда вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> метод, передавая указатель в текстовой метки и выбрать в контекстном меню команду.  
  
     Используйте эту информацию из этого вызова для выполнения определяет, какие бы действия текстовой метки вашей пользовательской команды.  
  
## <a name="see-also"></a>См. также  
 [С помощью текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Как: реализовать маркеры ошибки](../extensibility/how-to-implement-error-markers.md)   
 [Как: Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)   
 [Как: использовать маркеры текста](../extensibility/how-to-use-text-markers.md)