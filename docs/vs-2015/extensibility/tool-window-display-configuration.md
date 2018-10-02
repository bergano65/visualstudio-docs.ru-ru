---
title: Средство конфигурации отображения окна | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ff1e5b95b684c347ee1885d5dfddeb5eebb5a82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571279"
---
# <a name="tool-window-display-configuration"></a>Конфигурация отображения окна инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [конфигурацию отображаемое окно средства](https://docs.microsoft.com/visualstudio/extensibility/tool-window-display-configuration).  
  
Когда VSPackage регистрирует окно инструментов, положения по умолчанию, размер, стиль закрепления и другие сведения о видимости указывается в необязательных значений. Дополнительные сведения о регистрации окна инструментов, см. в разделе [средство Windows в реестре](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Сведения об отображении окна  
 Окно инструментов основного экрана конфигурация хранится в до шести необязательные значения:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|name|REG_SZ|«Короткое имя место»|Краткое имя, описывающее окна инструментов. Используется только для справки в реестре.|  
|Float|REG_SZ|«X1, Y1, X2, Y2»|Четыре значения с разделителями-запятыми. X1, Y1, — это координата верхнего левого угла окна инструментов. X2, Y2, — это координата нижний правый угол. Все значения являются в экранных координатах.|  
|Стиль|REG_SZ|«MDI»<br /><br /> «Плавающей»<br /><br /> «Связанный»<br /><br /> «С вкладками»<br /><br /> «AlwaysFloat»|Ключевое слово, указав первоначального отображения состояния окна инструментов.<br /><br /> «MDI» = прикреплено к окна интерфейса MDI.<br /><br /> «Float» = с плавающей запятой.<br /><br /> «Связанных» = соединенные еще одно окно (заданный в запись в окне).<br /><br /> «С вкладками» = в сочетании с другим окном инструментов.<br /><br /> «AlwaysFloat» = не может быть закреплено.<br /><br /> Дополнительные сведения см. в комментариях.|  
|Окно|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Идентификатор GUID окна, к которому могут быть связаны или с вкладками окне инструментов. Идентификатор GUID может принадлежать к одному из собственных windows или одно из окон в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среды разработки.|  
|Ориентация|REG_SZ|«Left»<br /><br /> «Right»<br /><br /> «Top»<br /><br /> «Bottom»|Ниже в разделе комментариев.|  
|DontForceCreate|REG_DWORD|0 или 1|Если эта запись присутствует и его значение не равно нулю, окна загружен, но отображаются не сразу.|  
  
### <a name="comments"></a>Комментарии  
 Ориентация определяет позицию, где закрепляет окно инструментов, при двойном щелчке его заголовок. Позиция задается относительно окна, указанную в запись в окне. Если запись стиля имеет значение «Связанный», операция ориентация может быть «Left», «Right», «Top» или «Bottom». Если операция стиля «С вкладками», ориентация, запись можно «оставить» или «Right» и указывает, где эта вкладка добавляется. Если запись стиля «Float», сначала располагается окно инструментов. При двойном щелчке заголовка, ориентацию и окно записи применяются, и в окне используется стиль «Вкладки». Если запись стиля «AlwaysFloat», не может быть закреплено окно инструментов. Если запись стиля «MDI», окно инструментов связана с области MDI, и запись в окне игнорируется.  
  
### <a name="example"></a>Пример  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Отображение окна инструментов  
 Значения в необязательный раздел видимость определяют параметры видимости окно инструментов. Имена значений используются для хранения идентификаторов GUID команды, требующие видимость окна. Если команда выполняется, интегрированной среды разработки гарантирует, что окно инструментов создается и становится видимым.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|Нет|Оставьте пустым.|  
|*\<ИДЕНТИФИКАТОР GUID &GT;*|Параметр DWORD или REG_SZ|0 или описательная строка.|Необязательный. Имя элемента должно быть GUID команды, требующие видимости. Значение содержит только строку информативные. Как правило, значение равно `reg_dword` присвоено значение 0.|  
  
### <a name="example"></a>Пример  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>См. также  
 [Основные сведения о пакетах VSPackage](../misc/vspackage-essentials.md)

