
VideoPicture pictq[VIDEO_PICTURE_QUEUE_SIZE];
int pictq_size, pictq_rindex, pictq_windex; // 初始值都是0
SDL_mutex *pictq_mutex;
SDL_cond *pictq_cond;

这里应该是一个环形队列
pictq_rindex 读到最后一个的时候回到第一个

这个队列里面放的是要播放的解码好的画面

SDL播放器线程主函数
event_loop
    video_refresh
        video_display
            video_image_display

queue_picture 会往pictq 里面丢数据


视频解码线程主函数
video_thread
    queue_picture