# tmux

�����ն˸��ù��������Ƽ�ʹ��tmux����Ȼ���๤�߱ȽϺõĻ���screen���������[screen](http://www.ibm.com/developerworks/cn/linux/l-cn-screen/) �����Ҹ��������Ƽ�tmux[ǿ���ķ�����]��
  
�������ֻ�Ƕ��ǩ�Ĺ��ܣ���ôputty���һЩ����Ҳ�������������߸ɴ�ʹ��xshell����Ȼtmux���๤�߲���������ô�򵥡�����һ��ѡ��ʹ��tmux/screen���ߵ�ԭ���ǣ���ʱ���ǻᾭ����ҪSSH����telentԶ�̵�¼��Linux����������һЩ������Ҫ��ʱ�����У�����ϵͳ���ݡ����ݴ���ȡ�ͨ����������Ƕ��ǿ�һ��Զ���ն˴��ڣ���Ϊִ��ʱ��Ƚϳ���һ����Ҫ�ȴ���ִ����ϣ��ڴ˹����в��ܹرմ��ڻ�������ԭ��Ͽ����ӣ��Ͽ�֮���Game Over�ˡ�������ܾ��е�����`nohup`��`setsid`�����ʵ���ˣ���`tmux/screen`��`nohup/setsid`�Ͷ��ǩ��һ��

## ��װ

��װ�Ļ�����Ͳ���˵���ˣ���ͬ��Linux���а���Ӧ�İ�������Ʋ�ͬ����װtmux�����ɡ�

## ʹ��ʵ��

### ��������

tmux��Ҫ�������¼���ģ�飺

*   session
    *   �Ự:һ�����������԰�������Ự
*   window
    *   ����:һ���Ự���԰����������
*   pane
    *   ���:һ�����ڿ��԰���������[ǿ���ķ���]

### �󶨿�ݼ�

�г���tmux�ļ�������ģ��֮�󣬾�Ҫ����ʵʵ���ڵĸɻ��ˣ���`screen`Ĭ�ϼ������̨��`Ctrl+a`��ͬ��tmuxĬ�ϵ���`Ctrl+b`��ʹ�ÿ�ݼ�֮��Ϳ���ִ��һЩ��Ӧ��ָ���ˡ���Ȼ����㲻ϰ��ʹ��`Ctrl+b`��Ҳ������`~/.tmux`�ļ��м����������ݰѿ�ݼ���Ϊ`Ctrl+a`��

``` bash
# Set prefix key to Ctrl-a
unbind-key C-b
set-option -g prefix C-a
```

�������еĲ������Ǽ������̨֮�󣬼�����`Ctrl+b`ǰ���²ſ���ʹ�õ������������ݼ�û�ģ����˵Ļ�����`Ctrl+b`����

### ��������

|?      | �г����п�ݼ�����q����                                                          |
|:----- | :------------------------------------------------------------------------------- |
|d      | ���뵱ǰ�Ự,����ʱ����Shell���棬����tmux attach�ܹ����½���֮ǰ�Ự            |
|s      | ѡ���л��Ự����ͬʱ�����˶���Ựʱʹ��                                       |
|D      | ѡ��Ҫ����ĻỰ����ͬʱ�����˶���Ựʱʹ��                                     |
|:      | ����������ģʽ����ʱ������֧�ֵ��������kill-server����tmux�Ự                |
|[      | ����ģʽ������ƶ�����������λ�ã��ո����ʼ�������ѡ���ƣ��س�ȷ�ϣ�q/Esc�˳�|
|]      | ����ճ��ģʽ��ճ��֮ǰ���Ƶ����ݣ���q/Esc�˳�                                    |
|~      | �г���ʾ��Ϣ���棻���а�����֮ǰtmux���صĸ�����ʾ��Ϣ                           |
|t      | ��ʾ��ǰ��ʱ��                                                                   |
|Ctrl+z | ����ǰ�Ự                                                                     |


  
### ���ڲ���
    
|   c           |�����´���                               |
| :-----------  | :-------------------------------------  |
|   &           |�رյ�ǰ����                             |
|   ���ּ�      |�л���ָ������                           |
|   p           |�л�����һ����                           |
|   n           |�л�����һ����                           |
|   l           |ǰ�󴰿ڼ以���л�                       |
|   w           |ͨ�������б��л�����                     |
|   ,           |��������ǰ���ڣ�����ʶ��                 |
|   .           |�޸ĵ�ǰ���ڱ�ţ��൱����������         |
|   f           |�����д����в��ҹؼ��ʣ����ڴ��ڶ����л� |

### ������:
    
|   "               |   ����ǰ������·���                                      |
|:--------------    |:--------------------------------------------------------  |
|   %               |   ����ǰ������ҷ���                                      |
|   x               |   �رյ�ǰ����                                            |
|   !               |   ����ǰ��������´���,���½�һ������,���н�������ǰ���  |   
|   Ctrl+�����     |   ��1����Ԫ��Ϊ��λ�ƶ���Ե�Ե�����ǰ����С             |
|   Alt+�����      |   ��5����Ԫ��Ϊ��λ�ƶ���Ե�Ե�����ǰ����С             |
|   �ո��          |   ������Ĭ����岼�����л������Ծ�֪����                  |
|   q               |   ��ʾ�����                                            |
|   o               |   ѡ��ǰ��������һ�����                                |
|   �����          |   �ƶ����ѡ���Ӧ���                                    |
|   {               |   ��ǰ�û���ǰ���                                        |
|   }               |   ����û���ǰ���                                        |
|   Alt+o           |   ��ʱ����ת��ǰ���ڵ����                                |
|   Ctrl+o          |   ˳ʱ����ת��ǰ���ڵ����                                |
|   z               |   tmux 1.8�����ԣ���󻯵�ǰ�������                      |
  
## .tmux.conf��������

��������ˣ��Լ���ô�������ô�á�������Ҫ��������`.tmux.conf`�����ļ������ã������г��ҵ������ļ���

``` bash
# Set prefix key to Ctrl-a
unbind-key C-b
set-option -g prefix C-a
bind-key C-a last-window # �����л�������ϰ��
bind-key a send-prefix   
# shell�µ�Ctrl+a�л��������ڴ�������ʧЧ���˴�����֮��Ctrl+a�ٰ�a�����л���shell����
 
# reload settings   # ���¶�ȡ���������ļ�
bind R source-file ~/.tmux.conf \; display-message "Config reloaded..."

# Ctrl-Left/Right cycles thru windows (no prefix) 
# ��ʹ��prefix����ʹ��Ctrl�����ҷ���������л�����
bind-key -n "C-Left" select-window -t :-
bind-key -n "C-Right" select-window -t :+

# displays 
bind-key * list-clients

set -g default-terminal "screen-256color"   # use 256 colors
set -g display-time 5000                    # status line messages display
set -g status-utf8 on                       # enable utf-8 
set -g history-limit 100000                 # scrollback buffer n lines
setw -g mode-keys vi                        # use vi mode

# start window indexing at one instead of zero ʹ���ڴ�1��ʼ��Ĭ�ϴ�0��ʼ 
set -g base-index 1 

# key bindings for horizontal and vertical panes
unbind %
bind | split-window -h      # ʹ��|�������������
unbind '"' 
bind - split-window -v      # ʹ��-�������������

# window title string (uses statusbar variables)
set -g set-titles-string '#T'

# status bar with load and time 
set -g status-bg blue 
set -g status-fg '#bbbbbb'
set -g status-left-fg green 
set -g status-left-bg blue
set -g status-right-fg green
set -g status-right-bg blue 
set -g status-left-length 90 
set -g status-right-length 90
set -g status-left '[#(whoami)]'
set -g status-right '[#(date +" %m-%d %H:%M ")]'
set -g status-justify "centre"
set -g window-status-format '#I #W'
set -g window-status-current-format ' #I #W '
setw -g window-status-current-bg blue
setw -g window-status-current-fg green

# pane border colors
set -g pane-active-border-fg '#55ff55'
set -g pane-border-fg '#555555'
```

ע������256 colors��Ҫ������Ӧ����`export ssh='TERM=xterm ssh'`

### ��������ִ��
  
����Ѿ��޸�prefix��λ`Ctrl+a`����`Ctrl+a`[Ĭ��Ctrl+b]������`:set synchronize-panes` ������:set sync [TAB]�����Զ�����
  
ȡ������ִ��ģʽ�ظ�֮ǰ��������

## �ű�������
  
�����½ű����ݼ��뵽`~/.bashrc`������ÿ�ε�¼���뵽tmux

``` bash
tmux_init()
{
    tmux new-session -s "kumu" -d -n "local"    # ����һ���Ự
    tmux new-window -n "other"          # ����һ������
    tmux split-window -h                # ����һ������
    tmux split-window -v "top"          # ����һ������,��ִ��top����
    tmux -2 attach-session -d           # tmux -2ǿ������256color�������ѿ�����tmux
}

# �ж��Ƿ����п�����tmux�Ự��û������
if which tmux 2>&1 >/dev/null; then
    test -z "$TMUX" && (tmux attach || tmux_init)
fi
```

## �ο��ĵ�
  
* [ʹ��tmux](https://wiki.freebsdchina.org/software/t/tmux)
* [archlinux tmux](https://wiki.archlinux.org/index.php/Tmux)
* [Tankywoo tmux wiki](http://wiki.wutianqi.com/software/tmux.html)
* [Tmux ʹ���ĵ�С�� ](http://www.lovelin.info/blog/2012/10/25/tmuxshi-yong-xin-de-xiao-ji/)
* [Tmux Openbsd Manual Pages](http://www.openbsd.org/cgi-bin/man.cgi?query=tmux&sektion=1)