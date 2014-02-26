TicTacToe---Iphone
==================

This is an iphone application for a Tic-Tac-Toe 2 player game 
//
//  ViewController.m
//  Tictactoe2player
//
//  Created by Dimple Badiani on 2/24/14.
//  Copyright (c) 2014 Dimple Badiani. All rights reserved.
//

#import "ViewController.h"

@interface ViewController ()

@end

@implementation ViewController
@synthesize  whoseTurn;
@synthesize s1,s2,s3,s4,s5,s6,s7,s8,s9;
@synthesize Owins, Xwins;

- (void) updatePlayerInfo{
    total++;
    NSLog(@"total - %d", total);

    if(playerToken == 1) {
        playerToken = 2;
        whoseTurn.text = @"It is O turn";
        NSLog(@"playerToken = %d", playerToken); }
    else if(playerToken == 2) { playerToken = 1; whoseTurn.text =@"It is X turn";
        NSLog(@"playerToken = %d", playerToken); }
    
    if ([self checkForWin]) {
        
        if (playerToken == 1)
        {
            UIAlertView *someonewon = [[UIAlertView
                                        alloc]initWithTitle:@"There's a winner!" message:@"Player O Won." delegate:self cancelButtonTitle:@"ok" otherButtonTitles: nil];
            numWinsO++;
            [Owins setText:[NSString stringWithFormat:@"%d", numWinsO]];
            [someonewon show];
        }
        else if (playerToken == 2) {
            UIAlertView *someonewon = [[UIAlertView
                                        alloc]initWithTitle:@"There's a winner!" message:@"Player X Won." delegate:self cancelButtonTitle:@"ok" otherButtonTitles: nil];
            numWinsX++;
            [Xwins setText:[NSString stringWithFormat:@"%d", numWinsX]];            [someonewon show];
            
        }
        else if (playerToken == 3) {
            UIAlertView *someonewon = [[UIAlertView
                                        alloc]initWithTitle:@"Tie Game!" message:@"Noone Won." delegate:self cancelButtonTitle:@"ok" otherButtonTitles: nil];
            [someonewon show];
        }
        [self resetBoard]; }


}


-(void) resetBoard{
    /// clear the images stored in the UIIMageView s1.image = NULL;
    s2.image = NULL;
    s3.image = NULL;
    s4.image = NULL;
    s5.image = NULL;
    s6.image = NULL;
    s7.image = NULL;
    s8.image = NULL;
    s9.image = NULL;
    // reset the player and update the label text
    playerToken= 1;
    whoseTurn.text = @"X goes first";
}


// method that will check to see if someone has won returns TRUE if someone wins
-(BOOL) checkForWin {
    
	// HORIZONTAL WINS
	if((s1.image == s2.image) & (s2.image == s3.image) & (s1.image != NULL))
	{
		return YES;
	}
	if((s4.image == s5.image) & (s5.image == s6.image) & (s4.image != NULL))
	{
		return YES;
	}
	if((s7.image == s8.image) & (s8.image == s9.image) & (s7.image != NULL))
	{
		return YES;
	}
	// VERTICAL WINS
	if((s1.image == s4.image) & (s4.image == s7.image) & (s1.image != NULL))
	{
		return YES;
	}
	if((s2.image == s5.image) & (s5.image == s8.image) & (s2.image != NULL))
	{
		return YES;
	}
	if((s3.image == s6.image) & (s6.image == s9.image) & (s3.image != NULL))
	{
		return YES;
	}
	// DIAGONAL WINS
	if((s1.image == s5.image) & (s5.image == s9.image) & (s1.image != NULL))
	{
		return YES;
	}
	if((s3.image == s5.image) & (s5.image == s7.image) & (s3.image != NULL))
	{
		return YES;
	}
	
	return NO;
}




// the touch event for the tic tac toe game
- (void)touchesBegan:(NSSet *)touches withEvent:(UIEvent *)event{
    UITouch *touch = [[event allTouches] anyObject];
    // check to see which UIImage view was touched
    if(CGRectContainsPoint([s1 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s1.image = xImg; }
        if(playerToken==2){ s1.image = oImg; } }
    if(CGRectContainsPoint([s2 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s2.image = xImg; }
        if(playerToken==2){ s2.image = oImg; } }
    if(CGRectContainsPoint([s3 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s3.image = xImg; }
        if(playerToken==2){ s3.image = oImg; } }
    if(CGRectContainsPoint([s4 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s4.image = xImg; }
        if(playerToken==2){ s4.image = oImg; } }
    if(CGRectContainsPoint([s5 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s5.image = xImg; }
        if(playerToken==2){ s5.image = oImg; } }
    if(CGRectContainsPoint([s6 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s6.image = xImg; }
        if(playerToken==2){ s6.image = oImg; } }
    if(CGRectContainsPoint([s7 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s7.image = xImg; }
        if(playerToken==2){ s7.image = oImg; } }
    if(CGRectContainsPoint([s8 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s8.image = xImg; }
        if(playerToken==2){ s8.image = oImg; } }
    if(CGRectContainsPoint([s9 frame], [touch locationInView:self.view])){
        if(playerToken==1){ s9.image = xImg; }
        if(playerToken==2){ s9.image = oImg; } }
    [self updatePlayerInfo];

}



- (void)viewDidLoad
{
    [super viewDidLoad];
	// add the images
    oImg = [UIImage imageNamed:@"O.png"];
    xImg = [UIImage imageNamed:@"X.png"];
    playerToken = 1;
    numWinsX = 0;
    numWinsO = 0;
    total=0;
    whoseTurn.text= @"X goes first";
}

- (void)didReceiveMemoryWarning
{
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}

- (IBAction)resetButton:(UIButton *)sender {
    
    [self resetBoard];
}
@end
