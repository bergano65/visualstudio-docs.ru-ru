---
title: "Получение шрифт и цвет шрифта текста окраски | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 22
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: d0b3d50ab2a78bf806be8c7339bb260746e1c457
ms.lasthandoff: 02/22/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Получение шрифта и цвет шрифта для текста цветом
Процесс, который подготавливает к просмотру или цветом текст отображается в элементы пользовательского интерфейса (UI) зависит от типа проекта, технологий и разработчиков предпочтений. **Шрифты и цвета** страница свойств содержит параметры.  
  
 Большинство реализаций, в которых отображаются цветом текста требуется `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` и соответствующие интерфейсы для представления, извлечение и сохранение текста для отображения параметров.  
  
> [!NOTE]
>  При настройке базового редактора (который поддерживает **EditorCategory текст**), настоятельно рекомендуется использовать технологию выделения цветом в языковой службы. Дополнительные сведения см. в разделе [шрифт и цвет Обзор](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Получение стандартный шрифт и цвет шрифта  
 Все **шрифты и цвета** должны быть указаны параметры окна, отображающие текст в **отображаемые элементы** одного **категории**. Дополнительные сведения см. в разделе [шрифты и цвета, среда, диалоговое окно «Параметры»](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Для выделения цветом, VSPackage необходимо получить текущий **шрифты и цвета** параметры. VSPackage это можно сделать одним из следующих способов, в зависимости от своих потребностей:  
  
-   Используйте механизм сохранения шрифт и цвет для получения хранимой или текущего состояния. Дополнительные сведения см. в разделе [параметров доступа к хранятся шрифта и](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>интерфейс службы, предоставляя данные шрифта и цвета, чтобы получить экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, если VSPackage не также поставщик шрифта и цвета.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
-   Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
 Чтобы гарантировать результаты, полученные путем опроса до даты, часто бывает полезно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>интерфейс, чтобы определить, требуется ли обновление до вызова методов извлечения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
 После получения информации шрифт и цвет, синтаксический анализ текста, отображаемого для указания на элементы, требующие окраски и отображения текста в окне, используя соответствующие шрифты и цвета.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Шрифты и текст](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Работа с цветом](/visual-cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (интерфейс графических устройств)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
