---
title: 'Пошаговое руководство: Запись графических сведений программными средствами | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7652f05bf6028dd7d5b14d207fdd0b83a73ef5ad
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227635"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Пошаговое руководство. Запись графических сведений программными средствами
С помощью диагностики графики [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно программно захватывать графические данные из приложения Direct3D.

Программный захват полезен в следующих сценариях.

- Начните захват программным образом, когда приложение графики не использует имеющуюся цепочку буферов, например при отрисовке до текстуры.

- Начните захват программным образом, если приложение вообще не выполняет отрисовку, например, когда оно использует DirectCompute для выполнения вычислений.

- Вызывайте `CaptureCurrentFrame`в случаях, когда проблемы с отрисовкой трудно предугадать и выявить при ручном тестировании, но можно прогнозировать программно при помощи информации о состоянии приложения во время выполнения.

## <a name="CaptureDX11_2"></a> Программный захват в Windows 10
В этой части пошагового руководства демонстрируется программный захват в приложениях, где применяется интерфейс API DirectX 11.2 в Windows 10, который использует метод надежного захвата.

В этом разделе рассмотрены следующие задачи:

- подготовка приложения к использованию программного захвата;

- получение интерфейса IDXGraphicsAnalysis;

- Захват графической информации

> [!NOTE]
> Предыдущих реализациях программного захвата использовались инструменты удаленной отладки для Visual Studio для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для предоставления функциональности захвата.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>подготовка приложения к использованию программного захвата;
Для использования программного захвата в приложении оно должно содержать необходимые заголовки. Эти заголовки являются частью пакета SDK для Windows 10.

##### <a name="to-include-programmatic-capture-headers"></a>Включение заголовков программного захвата

- Включите следующие заголовки в исходный файл, в котором будет определен интерфейс IDXGraphicsAnalysis:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Не включайте файл заголовка vsgcapture.h, который поддерживает программный захват в Windows 8.0 и более ранних версий, для выполнения программного захвата в приложениях Windows 10. Этот заголовок несовместим с DirectX 11.2. Если этот файл включен после заголовка d3d11_2.h включено, компилятор выдает предупреждение. Если vsgcapture.h включен перед d3d11_2.h, приложение не запустится.

    > [!NOTE]
    > Если пакет SDK DirectX от июня 2010 г. установлен на компьютере и путь включаемых файлов проекта содержит строку `%DXSDK_DIR%includex86`, переместите ее в конец пути включаемых файлов. Сделайте то же самое для пути к библиотеке.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>получение интерфейса IDXGraphicsAnalysis;
Чтобы получить возможность захватывать графические данные из DirectX 11.2, необходимо получить интерфейс отладки DXGI.

> [!IMPORTANT]
> При использовании программного захвата, необходимо запустить приложение в режиме диагностики графики (Alt + F5 в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) или в разделе [программа командной строки для захвата](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Получение интерфейса IDXGraphicsAnalysis

- Чтобы подключить интерфейс IDXGraphicsAnalysis к интерфейсу отладки DXGI, выполните указанный ниже код.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Не забудьте установить флажок `HRESULT` возвращаемые [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) позволит добиться допустимый интерфейс перед их использованием:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Если файл `DXGIGetDebugInterface1` возвращает `E_NOINTERFACE` , (`error: E_NOINTERFACE No such interface supported`), убедитесь, что приложение запущено в диагностике графики (клавиши ALT+F5 в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

### <a name="capturing-graphics-information"></a>Захват графической информации
Получив допустимый интерфейс `IDXGraphicsAnalysis` , можно использовать `BeginCapture` и `EndCapture` для захвата графических данных.

##### <a name="to-capture-graphics-information"></a>Захват графических данных

- Чтобы начать захват графических данных, используйте `BeginCapture`.

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    При вызове `BeginCapture` захват начинает выполняться немедленно, не дожидаясь начала следующего кадра. Захват заканчивается при выводе текущего кадра или при вызове `EndCapture`.

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- После вызова `EndCapture`, освободить объект graphics.

## <a name="next-steps"></a>Следующие шаги
В этом пошаговом руководстве было продемонстрировано, как захватывать графические данные программным путем. Далее можно перейти к рассмотрению следующего этапа.

- Узнайте, как анализировать захваченные графические данные с помощью средств диагностики графики. См. в разделе [Обзор](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>См. также раздел
[Пошаговое руководство. Запись сведений графики](walkthrough-capturing-graphics-information.md)  
[Capturing Graphics Information](capturing-graphics-information.md)  
[Программа командной строки для захвата](command-line-capture-tool.md)
