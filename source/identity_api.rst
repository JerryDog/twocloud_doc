


认证服务
====================

.. toctree::
   :maxdepth: 2
   :numbered:



概要
--------------------

认证服务提供认证、授权，基于 HTTP Basic Auth



用户账号(User)
--------------------

用户需要根据用户名和密码生成 token，并用 tokens 请求 API。 token 有效期为 24h


API规范
--------------------------

认证服务API入口与API列表如下：


    * API入口: http://tcapi.twocloud.cn
    * API列表:

+------------------+------------------------------+------------+--------------------------------+
|  资源            |  操作                        |  HTTP方法  |  URI路径                       |
+==================+==============================+============+================================+
|  Tokens (令牌)   |  获取 token                  |  POST      |  /twocloud/tokens             |
+------------------+------------------------------+------------+--------------------------------+


令牌 (Tokens)
--------------------------------------


认证并生成新令牌(已可用)

+------------+-------------------+---------------+
|  HTTP方法  |  URI路径          |  描述         |
+============+===================+===============+
|  POST      |  /twocloud/tokens |  获取令牌     |
+------------+-------------------+---------------+

请求参数

+-----------------------+----------+-----------------------------------------------------------------------------+
|  字段名               |  类型    |  描述                                                                       |
+=======================+==========+=============================================================================+
|  username             |  string  |  用户名                                                                     |
+-----------------------+----------+-----------------------------------------------------------------------------+
|  password             |  string  |  密码                                                                       |
+-----------------------+----------+-----------------------------------------------------------------------------+

请求样例

::

    
    curl -i -s \
         -u username:password \
         -X POST http://tcapi.twocloud.cn/twocloud/tokens


返回参数

+-------------------+-------------+-------------------------------------------------------------------------+
|  字段名           |  类型       |  描述                                                                   |
+===================+=============+=========================================================================+
|  duration         |  string     |  token 有效期                                                           |
+-------------------+-------------+-------------------------------------------------------------------------+
|  token            |  string     |  请求其他 API 所必须的 token                                            |
+-------------------+-------------+-------------------------------------------------------------------------+

返回样例

::

    HTTP/1.0 200 OK
    
    {
      "duration": 600,
      "token": "eyJhbGciOiJIUzI1NiIsImV4cCI6MTQ1NzUwOTgyMywiaWF0IjoxNDU3NTA5MjIzfQ.eyJpZCI6M30.0pD6WJR11H4I2bpIOlBfHvDsbYpBPEHaz8p1OARfbDk"
    }
