# Satellite Channel Structure

## Background
All defined satellites have a structure used to pass information between acquisition and tracking channel on hardware.
This structure defined the information for acquisition/tracking channel to search/lock the signal in the real-time.


## Declaration
```c
struct sv_signal
{
  struct list_head  list;
};

struct sv_ctrl
{
  struct sv_signal      sig;
  struct sv_search      *searchcfg;
  struct acq_channel    *acqchan;
  struct trk_channel    *trkchan;
#ifdef GLONASS
  int16_t               freqnum;
#endif /* GLONASS */
};

struct sv_channel
{
  struct sv_ctrl    svctrl;
  struct list_head  list;
  int16_t           lastqua;        // Previous satellite signal quality
  int16_t           pri;            // Priority of searching
};

void svchan_init(void);

/**
 * Add a satellite to search list.
 */
void svchan_add(struct sv_channel *svchan);

/**
 * Remove a satellite from search list.
 */
void svchan_remove(struct sv_channel *svchan);

/**
 * Perform searching for satellites in search list
 */
void svchan_search(void);

/**
 * Remove the satellite from acquisition/tracking, but keep it in search list.
 */
void svchan_kill(struct sv_ctrl *svctrl);

```

