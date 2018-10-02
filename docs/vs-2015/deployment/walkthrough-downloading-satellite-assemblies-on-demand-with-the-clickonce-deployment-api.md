---
title: 'Пошаговое руководство: Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: dfd9b73b7cd12108f86f566eb8d1d4a1c3823f4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557888"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Пошаговое руководство. Загрузка вспомогательных сборок по требованию с помощью интерфейса API технологии развертывания ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce](https://docs.microsoft.com/visualstudio/deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api).  
  
Приложения Windows Forms можно настроить для нескольких языков и региональных параметров, воспользовавшись вспомогательными сборками. *Вспомогательная сборка* — это сборка, содержащая ресурсы приложения для языка, отличного от языка и региональных параметров приложения по умолчанию.  
  
 Как уже говорилось в [локализация приложений ClickOnce](../deployment/localizing-clickonce-applications.md), может включать несколько вспомогательных сборок для нескольких языков и региональных параметров в пределах одного [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания. По умолчанию [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] загружает все вспомогательные сборки в развертывание на клиентском компьютере, хотя один клиент, вероятно, потребует только одну вспомогательную сборку.  
  
 Это пошаговое руководство показывает, как пометить вспомогательные сборки как необязательные и загрузить только сборку, необходимую клиентскому компьютеру для текущих настроек языка и региональных параметров. В следующей процедуре используются средства, доступные в [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Эту задачу также можно выполнить в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  См. также раздел [Пошаговое руководство. Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce и конструктора](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) или [Пошаговое руководство. Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce и конструктора](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  В целях тестирования в следующем примере кода программным образом задается следующий язык и региональные параметры: `ja-JP`. В подразделе «Дальнейшие действия» далее в этом разделе приводятся сведения о том, как настроить этот код для производственной среды.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Составители этого раздела исходили из того, что вы знаете, как добавить локализованные ресурсы в свое приложение с использованием Visual Studio. Подробные инструкции см. в разделе [Пошаговое руководство: локализация форм Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Загрузка вспомогательных сборок по требованию  
  
1.  Добавьте следующий код в приложение, чтобы включить загрузку вспомогательных сборок по требованию.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2.  Создайте вспомогательные сборки для приложения с помощью [Resgen.exe (генератор файлов ресурсов)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) или [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Создайте манифест приложения или откройте существующий манифест приложения с помощью MageUI.exe. Дополнительные сведения об использовании этого инструмента см. в разделе [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4.  Щелкните вкладку **Файлы** .  
  
5.  Щелкните кнопку **многоточие** (**...**) и выберите каталог, содержащий все сборки и файлы вашего приложения, включая вспомогательные сборки, созданные с помощью инструмента Resgen.exe. (Вспомогательная сборка будет иметь имя в формате *isoCode*\ApplicationName.Resources.dll, где *isoCode* — это идентификатор языка в формате RFC 1766.)  
  
6.  Щелкните **Заполнить** , чтобы добавить файлы в ваше развертывание.  
  
7.  Установите флажок **Необязательно** для каждой вспомогательной сборки.  
  
8.  Установите в поле группировки для каждой вспомогательной сборки соответствующий идентификатор языка по ISO. Например, для японской вспомогательной сборки нужно указать имя группы загрузки `ja-JP`. В результате код, добавленный вами в шаге 1, сможет загружать соответствующую вспомогательную сборку в зависимости от настройки свойства <xref:System.Threading.Thread.CurrentUICulture%2A> у пользователя.  
  
## <a name="next-steps"></a>Следующие шаги  
 В продуктивной среде, скорее всего, потребуется удалить строку в примере кода, задающую определенное значение для свойства <xref:System.Threading.Thread.CurrentUICulture%2A> , потому что на клиентских компьютерах правильное значение будет задаваться по умолчанию. Если приложение выполняется на клиентском компьютере с японским языком, например, свойство <xref:System.Threading.Thread.CurrentUICulture%2A> будет по умолчанию равно `ja-JP` . Программная установка этого значения — хороший способ проверить вспомогательные сборки перед развертыванием приложения.  
  
## <a name="see-also"></a>См. также  
 [Локализация приложений ClickOnce](../deployment/localizing-clickonce-applications.md)



