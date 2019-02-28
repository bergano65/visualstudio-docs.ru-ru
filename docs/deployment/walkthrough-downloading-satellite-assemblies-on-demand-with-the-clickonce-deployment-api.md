---
title: 'Пошаговое руководство: Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 515149f6e4e01c27d4076580f7fe405f3c8c5496
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637546"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Пошаговое руководство: Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce
Приложения Windows Forms можно настроить для нескольких языков и региональных параметров, воспользовавшись вспомогательными сборками. *Вспомогательная сборка* — это сборка, содержащая ресурсы приложения для языка, отличного от языка и региональных параметров приложения по умолчанию.

 Как уже говорилось в [локализация ClickOnce-приложений](../deployment/localizing-clickonce-applications.md), может включать несколько вспомогательных сборок для нескольких языков и региональных параметров в пределах одного [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания. По умолчанию [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] загружает все вспомогательные сборки в развертывание на клиентском компьютере, хотя один клиент, вероятно, потребует только одну вспомогательную сборку.

 Это пошаговое руководство показывает, как пометить вспомогательные сборки как необязательные и загрузить только сборку, необходимую клиентскому компьютеру для текущих настроек языка и региональных параметров. В следующей процедуре используются средства, доступные в [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Эту задачу также можно выполнить в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Также см. в разделе [Пошаговое руководство: Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce с помощью конструктора](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) или [Пошаговое руководство: Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce Конструктор](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

> [!NOTE]
>  В целях тестирования в следующем примере кода программным образом задается следующий язык и региональные параметры: `ja-JP`. В подразделе «Дальнейшие действия» далее в этом разделе приводятся сведения о том, как настроить этот код для производственной среды.

## <a name="prerequisites"></a>Предварительные требования
 Составители этого раздела исходили из того, что вы знаете, как добавить локализованные ресурсы в свое приложение с использованием Visual Studio. Подробные инструкции см. в разделе [Пошаговое руководство: локализация Windows forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).

### <a name="to-download-satellite-assemblies-on-demand"></a>Загрузка вспомогательных сборок по требованию

1. Добавьте следующий код в приложение, чтобы включить загрузку вспомогательных сборок по требованию.

    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]

2. Создайте вспомогательные сборки для приложения с помощью [Resgen.exe (генератор файлов ресурсов)](/dotnet/framework/tools/resgen-exe-resource-file-generator) или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

3. Создайте манифест приложения или откройте существующий манифест приложения с помощью *MageUI.exe*. Дополнительные сведения об использовании этого инструмента см. в разделе [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

4. Щелкните вкладку **Файлы** .

5. Щелкните кнопку **многоточие** (**...**) и выберите каталог, содержащий все сборки и файлы вашего приложения, включая вспомогательные сборки, созданные с помощью инструмента *Resgen.exe*. (Вспомогательная сборка будет иметь имя в формате *\<isoCode>\ApplicationName.resources.dll*, где \<isoCode> — это идентификатор языка в формате RFC 1766.)

6. Щелкните **Заполнить** , чтобы добавить файлы в ваше развертывание.

7. Установите флажок **Необязательно** для каждой вспомогательной сборки.

8. Установите в поле группировки для каждой вспомогательной сборки соответствующий идентификатор языка по ISO. Например, для японской вспомогательной сборки нужно указать имя группы загрузки `ja-JP`. В результате код, добавленный вами в шаге 1, сможет загружать соответствующую вспомогательную сборку в зависимости от настройки свойства <xref:System.Threading.Thread.CurrentUICulture%2A> у пользователя.

## <a name="next-steps"></a>Следующие шаги
 В продуктивной среде, скорее всего, потребуется удалить строку в примере кода, задающую определенное значение для свойства <xref:System.Threading.Thread.CurrentUICulture%2A> , потому что на клиентских компьютерах правильное значение будет задаваться по умолчанию. Если приложение выполняется на клиентском компьютере с японским языком, например, свойство <xref:System.Threading.Thread.CurrentUICulture%2A> будет по умолчанию равно `ja-JP` . Программная установка этого значения — хороший способ проверить вспомогательные сборки перед развертыванием приложения.

## <a name="see-also"></a>См. также
- [Локализация приложений ClickOnce](../deployment/localizing-clickonce-applications.md)