---
title: Получение сведений о шрифтах и цветах для цветовой раскраски текста | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696860"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Получение сведений о шрифте и цвете для цветового выделения текста
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Процесс, который визуализирует или отображает выделенный цветом текст в элементах ПОЛЬЗОВАТЕЛЬСКОГО интерфейса, зависит от типа проекта, его технологии и настроек разработчика. Параметры сохраняются на странице свойств **шрифты и цвета** .  
  
 Большинству реализаций, отображающих цветовой текст, требуются `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` и связанные интерфейсы для представления, извлечения и сохранения параметров отображения текста.  
  
> [!NOTE]
> При настройке основного редактора (который поддерживает **текст едиторкатегори**) настоятельно рекомендуется использовать технологию выделения цветом в языковой службе. Дополнительные сведения см. в разделе [Общие сведения о шрифтах и цветах](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Получение сведений о шрифтах и цветах по умолчанию  
 Все параметры **шрифтов и цветов** любого окна, отображающие текст, должны быть указаны в **отображаемых элементах** одной **категории**. Дополнительные сведения см. в разделе [шрифты и цвета, среда, диалоговое окно Параметры](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Чтобы зацветировать, VSPackage должен получить текущие настройки **шрифтов и цветов** . Пакет VSPackage может сделать это следующим образом в зависимости от потребностей:  
  
- Используйте механизм сохранения шрифта и цвета для получения сохраненного или текущего состояния. Дополнительные сведения см. в разделе [доступ к сохраненным параметрам шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс службы, предоставляющий данные о шрифтах и цветах, чтобы получить экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , если пакет VSPackage не является также поставщиком шрифтов и цветов.  
  
- Реализовать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
  Чтобы обеспечить актуальность результатов опроса, может быть полезно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуется ли обновление перед вызовом методов получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса.  
  
  После получения сведений о шрифтах и цветах следует проанализировать отображаемый текст, чтобы определить элементы, которым требуется выделение цветом, а затем отобразить текст в окне, используя соответствующие шрифты и цвета.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Использование шрифтов и текста](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Работа с цветом](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (интерфейс графических устройств)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
