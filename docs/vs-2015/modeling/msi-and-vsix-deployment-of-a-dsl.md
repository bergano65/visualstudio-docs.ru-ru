---
title: Развертывание VSIX для DSL | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916549"
---
# <a name="vsix-deployment-of-a-dsl"></a>Развертывание VSIX для DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете установить доменный язык на своем компьютере или на других компьютерах. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] уже должен быть установлен на конечном компьютере.

## <a name="installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Установка и удаление DSL с помощью VSX
 При установке DSL этим методом пользователь может открыть файл DSL из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , но файл нельзя открыть из проводника Windows.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>Установка DSL с помощью VSIX

1. На компьютере найдите **VSIX** файл, созданный проектом пакета DSL.

    1. В **Обозреватель решений**щелкните правой кнопкой мыши проект **DslPackage** и выберите пункт **Открыть папку в проводнике Windows**.

    2. Откройте файл ** \\ \* \\ bin**_йоурпрожект_**. DslPackage. VSIX**

2. Скопируйте **VSIX** файл на конечный компьютер, на который необходимо установить DSL. Это может быть как ваш собственный компьютер, так и любой другой.

    - На целевом компьютере должен быть установлен один из выпусков [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , поддерживающий DSL во время выполнения. Дополнительные сведения см. в разделе [Поддерживаемые выпуски Visual Studio для визуализации & моделирования SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - На целевом компьютере должен быть один из выпусков, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] указанных в **дслпаккаже\саурце.екстенсионс.манифест**.

3. На целевом компьютере дважды щелкните **VSIX** -файл.

     Откроется**установщик расширений Visual Studio** , который устанавливает расширение.

4. Запустите или перезапустите [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. Чтобы протестировать DSL, используйте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для создания нового файла с расширением, определенным для вашего DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Удаление DSL, установленного с помощью VSX

1. В меню **Сервис** выберите пункт **Диспетчер расширений**.

2. Разверните узел **Установленные расширения**.

3. Выберите расширение, в котором определен DSL, и нажмите кнопку **Удалить**.

   В редких случаях не удается загрузить неисправное расширение, в результате чего в окне ошибок создается отчет, который не отображается в диспетчере расширений. В этом случае расширение можно удалить, удалив файл из следующей папки:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**
