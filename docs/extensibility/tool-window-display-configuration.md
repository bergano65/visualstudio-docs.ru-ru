---
title: "Настройка отображения окна инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9478ffb6ffc1fcd2204065ff4fb7cb113ab88ba4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-window-display-configuration"></a>Настройка отображения окна средства
Когда VSPackage регистрирует окна инструментов, положение по умолчанию, размер, стиль закрепления и другие сведения о видимости указывается в необязательных значений. Дополнительные сведения о регистрации окна средства просмотра [окна инструментов в реестре](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Отображение информации в окне  
 Настройка основного экрана окно инструментов хранится в до шести необязательных значений:  
  
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
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|Имя|REG_SZ|«Краткое имя здесь»|Краткое имя, описывающее окно инструментов. Используется только для ссылки в реестре.|  
|Float|REG_SZ|«X1, Y1, X2, Y2»|Четыре значения запятыми. X1, Y1 имеет координаты верхнего левого угла окна инструмента. X2, Y2 имеет координату нижнего правого угла. Все значения являются в экранных координатах.|  
|Стиль|REG_SZ|«MDI»<br /><br /> «Плавающей»<br /><br /> «Связано»<br /><br /> «С вкладками»<br /><br /> «AlwaysFloat»|Ключевое слово, указав первоначального отображения состояния окна инструментов.<br /><br /> «MDI» = прикреплено к окну MDI.<br /><br /> «Float» = с плавающей запятой.<br /><br /> «Связано» = связан с другим окном (указанный в запись в окне).<br /><br /> «С вкладками» = вместе с другим окном инструментов.<br /><br /> «AlwaysFloat» = нельзя закрепить.<br /><br /> Дополнительные сведения см. ниже в разделе комментариев.|  
|Окно|REG_SZ|*\<ИДЕНТИФИКАТОР GUID НАСТРОЕК*|Идентификатор GUID, окна, к которому могут быть связаны или вкладок окна средства. Идентификатор GUID могут входить в один из собственных windows или одно из окон в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.|  
|Ориентация|REG_SZ|«Левый»<br /><br /> «Правой»<br /><br /> «Начало»<br /><br /> «Вниз»|Ниже в разделе комментариев.|  
|DontForceCreate|REG_DWORD|0 или 1|Если его значение не равно нулю, а эта запись отсутствует, окно загружен, но отображаться не сразу.|  
  
### <a name="comments"></a>Комментарии  
 Операция ориентацию определяет положение, где закрепляет окно инструментов при двойном щелчке его заголовок. Позиция задается относительно окна, указанную в запись в окне. Если элемент стиля «Связанный», операция ориентацию может быть «Влево», «Вправо», «Начало» или «Вниз». Если элемент стиля «С вкладками», ориентацию запись можно «оставить» или «Правой» и указывает, где эта вкладка добавляется. Если запись стиля «Float», сначала располагается окно средства. При двойном щелчке заголовка применяются операции ориентацию и окна и окна используется стиль «Вкладки». Если элемент стиля «AlwaysFloat», нельзя закрепить окно инструментов. Если запись стиля «MDI», окно инструментов связана области MDI, и запись в окне игнорируется.  
  
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
 Значения в необязательный раздел видимость определяют параметры видимости окно инструментов. Имена значений используются для хранения идентификаторов GUID для команды, требующие видимость окна. Если выполнена команда интегрированной среды разработки гарантирует, что окно инструментов создается и становится видимым.  
  
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
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|Нет|Оставьте пустым.|  
|*\<ИДЕНТИФИКАТОР GUID НАСТРОЕК*|Параметр DWORD или REG_SZ|0 или описательная строка.|Необязательный. Имя входа должно быть GUID команды, требующие видимость. Значение содержит только информативной строкой. Как правило, является значение `reg_dword` равным 0.|  
  
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
