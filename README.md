# やりたいこと

1. camera_node.pyとaudio_node.pyを試作して、pcのcamera映像をWebRTCできるかを確認する。

	1-1. 参考URL:https://opensource-robotics.tokyo.jp/?p=8267
	
	1-2. $ sudo apt install ros-jazzy-v4l2-camera
	
	1-3. git clone --branch ${ROS_DISTRO} https://gitlab.com/boldhearts/ros2_v4l2_camera.git src/v4l2_camera
rosdep install --from-paths src/v4l2_camera --ignore-src -r -y
colcon build

	1-4. pip install catkin_pkg
	catkin_pkg モジュールがPython環境にインストールされていないため、ament_cmake が package.xml を処理できずにエラーになった。先頭のコードを実行

	1-5. sudo apt install python3-yaml
	launch-rosはpyyamlに依存しているが、pyyamlが不足していたためインストール。

	1-7. ros2 run v4l2_camera v4l2_camera_node
	実行したがカメラが認識されていない。WSLはUSBを認識させてあげなければならない。そのため、以下の参考URLで認識できるようにする。https://learn.microsoft.com/ja-jp/windows/wsl/connect-usb

	1-8.実行権限などにより仕方なくroot権限でsudo ros2 run v4l2_camera v4l2_camera_nodeを実行した。別のターミナルを開きsudo apt-get install ros-${ROS_DISTRO}-rqt-image-view
ros2 run rqt_image_view rqt_image_viewを実行したが、動画が表示されなかった。

	1-9. WSLでGUIを動作させるためにXserverが必要かもしれないので、インストールしてみる。


	1-10. rqtのプルダウンの/image_rawに切り替えても表示がされない。publishとsubscribeはできていることが確認できたが画像が表示できない。
	
	1-11. どうやってもrqtやrviz2で動画を確認できなかった。WSLでのやり方で何が足りないのかがわからない。いったん、今日はあきらめる。
2. roslibjsでRPLiDARのスキャンデータを取得し、既存のlidar.jsに組み込めるか試す。

	2-1. イメージがわかなくなってしまったので全体の把握に努める。
