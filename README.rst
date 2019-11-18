=========
chatspace
=========

.. image:: https://travis-ci.com/pingpong-ai/chatspace.svg?branch=master
  :target: https://travis-ci.com/pingpong-ai/chatspace
.. image:: https://codecov.io/gh/pingpong-ai/chatspace/branch/master/graph/badge.svg
  :target: https://codecov.io/gh/pingpong-ai/chatspace


핑퐁에서 만든 채팅체랑 잘 맞는 띄어쓰기 모델! 🔪😎

Getting Started
---------------

.. code-block:: python

    from chatspace import ChatSpace

    spacer = ChatSpace()
    spacer.space("안녕 만나서반가워 내이름은뽀로로라고해")
    # '안녕 만나서 반가워 내 이름은 뽀로로라고 해'

Requirements
------------

.. code-block:: text

    torch


Installation
------------


From GitHub
~~~~~~~~~~~

.. code-block:: shell

    pip install chatspace

Detail Usage
------------

Batch Inference
~~~~~~~~~~~~~~~

.. code-block:: python

    from chatspace import ChatSpace

    spacer = ChatSpace()
    texts = ["안녕 만나서반가워 내이름은뽀로로라고해", "와진짜대박", ...]

    spacer.space(texts, batch_size=64)
    # ['안녕 만나서 반가워 내 이름은 뽀로로라고 해', '와 진짜 대박', ...]

Iterative
~~~~~~~~~

.. code-block:: python

    from chatspace import ChatSpace

    spacer = ChatSpace()
    texts = ["안녕 만나서반가워 내이름은뽀로로라고해", "와진짜대박", ...]

    for origin_text in spacer.space_iter(texts):
        print(origin_text)

    # '안녕 만나서 반가워 내 이름은 뽀로로라고 해'
    # '와 진짜 대박'
    # ...

Advanced (Custom Vocab/Custom Device)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

    from chatspace import ChatSpace
    import torch

    # 원하는 torch.device 로 chatspace 모델을 옮기고 실행할 수 있음
    custom_device = torch.device("cuda:0")
    spacer = ChatSpace(device=custom_device)

    # 띄어쓰기를 원치않는 단어들을 설정할 수 있음
    texts = ["안녕 만나서반가워 내이름은뽀로로라고해", "와진짜대박", ...]
    spacer.space(texts, custom_vocab=["내이름", "진짜대박"])

    # '안녕 만나서 반가워 내이름은 뽀로로라고 해'
    # '와 진짜대박'
    # ...


Authors
-------

**Pingpong AI Research, Machine Learning Engineers**

- Researched By `서수인 Suin Seo`_
- Developed By `김준성 Junseong Kim`_

.. _서수인 Suin Seo: suin@scatterlab.co.kr
.. _김준성 Junseong Kim: junseong.kim@scatterlab.co.kr

License
-------

Copyright 2019 Pingpong AI Research, ScatterLab `Apache License 2.0 <https://github.com/pingpong-ai/chatspace/blob/master/LICENSE>`_
