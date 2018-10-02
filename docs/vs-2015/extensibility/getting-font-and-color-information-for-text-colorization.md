---
title: Начало шрифт и цвет шрифта для цветовое выделение текста | Документация Майкрософт
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
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d4b5ebbaea2b146f1b853360b88bad2363ce77f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573290"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Начало шрифт и цвет шрифта для цветовое выделение текста
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [начало шрифт и цвет шрифта для цветовое выделение текста](https://docs.microsoft.com/visualstudio/extensibility/getting-font-and-color-information-for-text-colorization).  
  
Процесс, который выполняет визуализацию или отображает цветом текста в элементы пользовательского интерфейса (UI) зависит от типа проекта, технологий и разработчиков предпочтений. **Шрифты и цвета** страницу свойств сохраняет параметры.  
  
 Большинство реализаций, которые отображают цветом текст требуется `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` и связанные интерфейсы для параметры отображения представления, получение и сохранение текста.  
  
> [!NOTE]
>  При настройке базового редактора (который поддерживает **EditorCategory текст**), настоятельно рекомендуется использовать технологию выделение цветом в языковой службе. Дополнительные сведения см. в разделе [шрифт и цвет Обзор](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Начало стандартный шрифт и цвет шрифта  
 Все **шрифты и цвета** следует указать параметры окна, отображающие текст в **отображаемые элементы** одного **категории**. Дополнительные сведения см. в разделе [шрифты и цвета, среда, диалоговое окно параметров](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Для выделения цветом, VSPackage должен получить текущий **шрифты и цвета** параметры. VSPackage это можно сделать следующими способами, в зависимости от его потребностей:  
  
-   Используйте механизм сохраняемости шрифта и цвета для получения хранимой или в текущем состоянии. Дополнительные сведения см. в разделе [параметры доступа к хранятся шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс службы, предоставляющего данные шрифта и цвета для получения экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, если пакет VSPackage не также поставщика шрифта или цвета.  
  
-   Реализовать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
 Чтобы убедиться, что результаты, полученные путем опроса, актуальные, часто бывает полезно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуется ли обновление до вызова методов извлечения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.  
  
 После получения данные шрифта и цвета, синтаксический анализ текста, отображаемого для идентификации элементов, требующих Раскраска и затем отобразите текст в окне, используя соответствующие шрифты и цвета.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Шрифты и текст](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Работа с цветом](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (интерфейс графических устройств)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)

